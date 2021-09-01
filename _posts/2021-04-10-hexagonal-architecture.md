---
layout: post
title: Hexagonal (Ports & Adapters) Architecture
tags:
 - 8 min read
---

## Introduction
---

In this article, I would like to talk about Hexagonal Architecture, an architecture really interesting where we apply examples in PHP. This architecture is also known as Ports & Adapters because it's easier to identify and remember. **Ports** mean Interfaces. **Adapters** mean implementations of those interfaces.

> A particular tip: **Domain-Driven Design** supports this architecture because of its maintainability, testing, simplicity, decoupling and, so on. 

When we work with APIs, SDKs, or scalable web applications, our first choice is to work with a robust framework and, most of them depend on the programming language. Usually, some frameworks implement MVC or other architectures patterns and, we don't worry about them. However, Hexagonal Architecture provides us a good design, easy to adapt, easy to scale, and helps us to divide our responsibilities into layers.

---

## Layers and Dependency Rule
---

Ports & Adapters have predefined layers in which are: **Infrastructure, Application, and Domain**.
This rule says the code that belongs to each layer must only know the objects or components from the next layer.
<br>
<br>
`Infrastructure (next layer) -> Application (next layer) -> Domain`
<br>
<br>
> We can create layers in a customizable way. It always depends on our domain context.

---

## Domain
---

This layer is all about our context or core domain, business rules (User, Product, Car).
- Domain models or entities.
- Value Objects.
- Ports (UserRepositoy, ProductRepository).
<br>
<br>
> The domain layer doesn't have any dependency on the other layers.

**A few examples:**

```php
<?php

declare(strict_types=1);

namespace HexagonalArchitecture\Products\Domain;

final class Product
{
    public function __construct(
        private string $id, 
        private string $name, 
        private string $description)
    {
        $this->id = $id;
        $this->name = $name;
        $this->description = $description;
    }

    public static function fromPrimitives(array $primitives): Product
    {
        return new self(
            $primitives['id'], 
            $primitives['name'], 
            $primitives['description']);
    }

    public function toPrimitives(): array
    {
        return [
            'id'            => $this->id,
            'name'          => $this->name,
            'description'   => $this->description,
        ];
    }

    public function id(): string
    {
        return $this->id;
    }

    public function name(): string
    {
        return $this->name;
    }

    public function description(): string
    {
        return $this->duration;
    }
}
```

```php
<?php

declare(strict_types=1);

namespace HexagonalArchitecture\Products\Domain;

use Shared\Domain\Criteria\Criteria;

interface ProductRepository
{
    public function save(Product $product): void;

    public function searchAll(): array;

    public function matching(Criteria $criteria): array;
}
```

---

## Application
---

This layer is our uses cases, actions (User registration, Post products, Add products).
- Business Behavior (Criterias, Responses, Validations).
- Injections of Domain Repositories.
- Services.
<br>
<br>
> The application layer doesn't have any dependency on the other layers.

**A few examples:**

```php
<?php

declare(strict_types=1);

namespace HexagonalArchitecture\Products\Application\Create;

use HexagonalArchitecture\Products\Domain\Product;
use HexagonalArchitecture\Products\Domain\ProductRepository;

final class ProductCreator
{
    public function __construct(private ProductRepository $repository)
    {
    }

    public function create(string $id, string $name, string $description): void
    {
        $this->repository->save(new Product($id, $name, $description));
    }
}
```

```php
<?php

declare(strict_types=1);

namespace HexagonalArchitecture\Products\Application;

final class ProductResponse
{
    public function __construct(
        private string $id, 
        private string $name, 
        private string $description)
    {
    }

    public function id(): string
    {
        return $this->id;
    }

    public function name(): string
    {
        return $this->name;
    }

    public function description(): string
    {
        return $this->description;
    }
}
```

---

## Infrastructure
---

This layer is where the interfaces' implementations live, considering we define our interfaces in the domain layer.
(Publish events, external states, controllers).
- Adapters (MySqlUserRepository, MySqlProductRepository).
- Senders and Credentials from external APIs.
- Wrappers.

**An example with a simple product:**

```php
<?php

declare(strict_types=1);

namespace HexagonalArchitecture\Products\Infrastructure\Persistence;

use HexagonalArchitecture\Products\Domain\Product;
use HexagonalArchitecture\Products\Domain\ProductRepository;
use HexagonalArchitecture\Shared\Domain\Criteria\Criteria;
use HexagonalArchitecture\Shared\Infrastructure\Persistence\Doctrine\DoctrineCriteriaConverter;
use HexagonalArchitecture\Shared\Infrastructure\Persistence\Doctrine\DoctrineRepository;

final class MySqlProductRepository extends DoctrineRepository implements ProductRepository
{
    public function save(Product $product): void
    {
        $this->persist($product);
    }

    public function searchAll(): array
    {
        return $this->repository(Product::class)->findAll();
    }

    public function matching(Criteria $criteria): array
    {
        $doctrineCriteria = DoctrineCriteriaConverter::convert($criteria);

        return $this->repository(Product::class)->matching($doctrineCriteria)->toArray();
    }
}
```

## Testing
---

- For **Application and Domain Layers**. We create unit tests and mock the ports.
- For **Infrastructure Layer**. We don't mock concrete implementations. We create integration tests to validate repository methods.

> We can apply **ObjectMother** for testing purposes. An **ObjectMother** provides us a factory class that has static methods letting us semantically instance the class.


**A few examples:**

```php
<?php

declare(strict_types=1);

namespace HexagonalArchitecture\Tests\Products\Domain;

use HexagonalArchitecture\Products\Domain\Product;
use HexagonalArchitecture\Tests\Shared\Domain\DescriptionMother;
use HexagonalArchitecture\Tests\Shared\Domain\UuidMother;
use HexagonalArchitecture\Tests\Shared\Domain\WordMother;

final class ProductMother
{
    public static function create(
        ?string $id = null, 
        ?string $name = null, 
        ?string $description = null): Product
    {
        return new Product(
            $id ?? UuidMother::create(), 
            $name ?? WordMother::create(), 
            $description ?? DescriptionMother::create());
    }
}   
```

```php
<?php

declare(strict_types=1);

namespace HexagonalArchitecture\Products\Infrastructure;

use HexagonalArchitecture\Tests\Products\Domain\ProductMother;
use HexagonalArchitecture\Tests\Shared\Domain\Criteria\CriteriaMother;

final class MySqlProductRepositoryTest
{
    /** @test */
    public function it_should_save_a_valid_product(): void
    {
        $this->mySqlRepository()->save(ProductMother::create());
    }

    /** @test */
    public function it_should_search_all_existing_products(): void
    {
        $existingProduct        = ProductMother::create();
        $anotherExistingProduct = ProductMother::create();
        $existingProducts       = [$existingProduct, $anotherExistingProduct];

        $this->mySqlRepository()->save($existingProduct);
        $this->mySqlRepository()->save($anotherExistingProduct);

        $this->assertSimilar($existingProducts, $this->mySqlRepository()->searchAll());
    }

    /** @test */
    public function it_should_search_all_existing_products_with_an_empty_criteria(): void
    {
        $existingProduct        = ProductMother::create();
        $anotherExistingProduct = ProductMother::create();
        $existingProducts       = [$existingProduct, $anotherExistingProduct];

        $this->mySqlRepository()->save($existingProduct);
        $this->mySqlRepository()->save($anotherExistingProduct);
        $this->clearUnitOfWork();

        $this->assertSimilar($existingProducts, 
        $this->mySqlRepository()->matching(CriteriaMother::empty()));
    }
}  
```

## Directories
---
Finally, our source code's directory looks like this:

```
HexagonalArchitecture
│  
└─── Application
│   │   ProductCreator.php
│   │   ProductResponse.php
│   
└─── Domain
│   │   Product.php
│   │   ProductRepository.php
│   
└─── Infrastructure
    │   MySqlProductRepository.php

```