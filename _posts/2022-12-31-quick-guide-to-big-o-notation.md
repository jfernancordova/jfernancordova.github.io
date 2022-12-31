---
layout: post
title: Quick Guide To Big O Notation
tags:
 - 10 min read
---

## Introduction
---

When we develop a feature, there are many alternatives that may be complex or demand a deeper knowledge, therefore we tend to build any solution in order to complete the requirement, we are quite certain it will work because all the uses cases we implement are testeable and reliable. 
However, when this feature is released, everything appears to be fine, as the company/startup/client you work for grows and the input size grows due to the new users, the application suddenly becomes very slow, the SRE's or DevOps's discover the bug and it appears that there is a feature whose performance is poor.

When this type of issue arises, we begin learning about new concepts related computer science and software engineering, we ask ourselves something like:

- How could we know if any feature we implement is fast and it is going to be ok if the input size grows?
- How could we know the complexity of an algorithm?

The simple answer is **Big O notation**, before we go any further. I'd like to share this quote: 

> Pragmatic Programmers estimate the resources that algorithms use—time, processor, memory, and so on.

**Chapter 3: The Basic Tools** from [The Pragmatic Programmer](https://www.amazon.com/Pragmatic-Programmer-journey-mastery-Anniversary/dp/0135957052).


<br>

## What is Big O Notation?
---

- It is a tool used to compare the efficiency of different algorithms.
- It helps us to describe the complexity of an algorithm. 
- It gives us a estimation of an algorithm's running time.
- It describes the **worst case scenario** which measures the maximum amount of time that an algorithm will take to execute, given the largest possible input.

### Key concepts:

- <em>Complexity Analysis:</em> Describes how efficient an algorithm is (time + space).
- <em>Time Complexity:</em> Measures how fast an algorithm is.
- <em>Space Complexity:</em> Measures how much memory will take up.

### Key rules:

- <em>Ignore the constants:</em> constant values are ignored because it doesn't affect the growth rate of the function as the input size becomes very large.

<br>

## Common Complexities
---

I'll include some golang snippets to help clarify them.

- ### O(1): Constant Time

    It means that the running time is independent of the size of the input. No matter how large the input is for this complexity. 
    - Example: <em>accessing a value with an array index.</em>
    - A quick problem:
  
    ```go
        /*
            Given two non-negative integers low and high. 
            Return the count of odd numbers between low and high (inclusive).
            
            O(1) time | O(1) space
        */
        func countOdds(low int, high int) int {
            if low&1 == 0 {
                low++
            }

            if low > high {
                return 0
            }

            return (high-low)/2 + 1
        }
    ```

- ### O(n): Linear Time

    It means that the running time of our algorithms is proportional to the size of the input.
    - Example: <em>Loop to print out the values of an array</em>.
    - A quick problem:

    ```go
        /*
            Given a string s, find the first non-repeating character in 
            it and return its index. If it does not exist, return -1.
            
            O(n) time | O(1) space
        */
        func firstUniqChar(s string) int {
            nonRepeated := make(map[rune]int)
            for _, char := range s {
                nonRepeated[char]++
            }

            for i, char := range s {
                if nonRepeated[char] == 1 {
                    return i
                }
            }

            return -1
        }
    ```

- ### O(n^2): Cuadratic Time

    It means that the running time is proportional to the square of the size of the input.
    - Example: <em>[Bubble Sort](https://en.wikipedia.org/wiki/Bubble_sort)</em>.
    - A quick problem:

    ```go
        /*
            Bubble Sort is the simplest sorting algorithm that works 
            by repeatedly swapping the adjacent elements 
            if they are in the wrong order.
            
            O(n^2) time | O(1) space
        */
        func bubbleSort(values []int) []int {
            isSorted := false
            counter := 0
            for !isSorted {
                isSorted = true
                for i := 0; i < len(values)-1-counter; i++ {
                    if values[i] > values[i+1] {
                        values[i], values[i+1] = values[i+1], values[i]
                        isSorted = false
                    }
                }
                counter++
            }
            return values
        }
    ```

- ### O(log n): Logarithmic Time

    It means that the running time grows at a slower rate as the size of the input grows.
    - Example: <em>[Binary Search](https://en.wikipedia.org/wiki/Binary_search_algorithm)</em>.
  
    ```go
        /*
            Given an array of integers nums which is sorted in ascending order, 
            and an integer target, write a function to search
            target in nums. If target exists, then return its index. 
            Otherwise, return -1.
            
            O(log(n)) time | O(1) space
        */
        func search(nums []int, target int) int {
            return binarySearch(nums, target, 0, len(nums)-1)
        }

        func binarySearch(nums []int, target int, left int, right int) int {
            for left <= right {
                middle := (left + right) / 2
                if target == nums[middle] {
                    return middle
                } else if target > nums[middle] {
                    left = middle + 1
                } else {
                    right = middle - 1
                }
            }
            return -1
        }
    ```

- ### O(n log n): Logarithmic Time

    It means that the running time is O(log n) plus a linear operation.
    - Example: <em>[Merge sort](https://en.wikipedia.org/wiki/Merge_sort)</em>.
    - A quick problem:

    ```go
        /*
            Given an integer array nums, return the largest perimeter of a triangle 
            with a non-zero area, formed from three of these
            lengths. If it is impossible to form any triangle of a 
            non-zero area, return 0.

            O(nlog(n)) time | O(1) space
        */
        func largestPerimeter(nums []int) int {
            sort.Ints(nums)
            for i := len(nums) - 3; i >= 0; i-- {
                if nums[i]+nums[i+1] > nums[i+2] {
                    return nums[i] + nums[i+1] + nums[i+2]
                }
            }
            return 0
        }
    ```


- ### O(2^n): Exponential Time

    It means that the running time increases exponentially as the input size increases.
    - Example: <em>[Fibonacci](https://en.wikipedia.org/wiki/Fibonacci_number)</em>.
  
    ```go
        /*
            The Fibonacci numbers, commonly denoted F(n) form a sequence, 
            called the Fibonacci sequence, such that each number is
            the sum of the two preceding ones, starting from 0 and 1.
            
            O(n) time | O(1) space
        */
        func fib(n int) int {
            result := 0
            if n > 2 {
                result = fib(n-1) + fib(n-2)
            } else if n == 1 || n == 2 {
                result = 1
            }
            return result
        }
    ```


- ### O(n!): Factorial Time

    It means that the running time which grows as the factorial of the input size.
    - A quick problem:

    ```go
        /*
            O(n!) time | O(1) space
        */
        func nRuntime(n int) {
            for i:= 0; i < n; i++ {
                nRuntime(n-1)
            }
        }
    ```

### Sequence:

Once we understand these complexities, we must be certain of the sequence from dreadful to good:

 <p style="text-align:center">
<code>O(1) < O(logn) < O(n) < O(nlogn) < O(n^2) < O (2^n) < O(n!)</code>
</p>

### Key concept:

- <em>Size of the input:</em> Number of items that our algorithm will process.

<br>

## Phone Book Example
---

This is a clever example of how to use these complexities; it may be the most human-friendly explanation; I strongly recommend that you read it.

[The Yellow Pages](https://stackoverflow.com/a/2307314/8333846).

<br>

## Big-O Cheat Sheet
---

All of these concepts are difficult to grasp, thus this [Cheat Sheet](https://www.bigocheatsheet.com/) is the finest resource I've discovered for refreshing our memory every time we need to utilize it.