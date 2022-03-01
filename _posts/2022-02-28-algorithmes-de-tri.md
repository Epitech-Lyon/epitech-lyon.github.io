---
layout: post
title:  "Sorting algorithms"
author:
    - adrien.michaud@epitech.eu
    - basile.seroul@epitech.eu
categories: [ experience ]
image: assets/images/sorting-algorithms/poster.jpg
published: true
comments: false
---

In computer science, arranging elements in an ordered sequence is called "sorting". It is a very a common operation in many applications and efficient algorithmshave been developed to perform it.

The most common uses of sorted sequences are :
- making lookup or search efficient.
- making merging of sequences efficient.
- enabling processing of data in a defined order.

For example, you might want to give priority to people who have been customers the longest, but also to people who have spent a lot of money or even to people who bought something yesterday. So you have to sort them by different criteria. Sorting is very critical for information systems performance, since it is quicker to find an element in an ordered list than in an unordered one. 

This article discusses sorting strategies and explains how to evaluate the performances of the corresponding algorithms.

## What does a sorting algorithm depend on?

A sorting algorithm depends on two factors : time complexity and space complexity. We can also talk about the stability of the algorithm.

*Time complexity* is the computational complexity that describes the amount of computer time it takes to run an algorithm. For example, `O(log N)` means time goes up linearly while the `N` goes up exponentially. So if it takes 1 second to compute 10 elements, it will take 2 seconds to compute 100 elements, 3 seconds to compute 1000 elements, and so on. *Space complexity* measures the total amount of memory that an algorithm or operation needs to run according to its input size.

The *stability* of a sorting algorithm is concerned with how the algorithm treats equal (or repeated) elements. Stable sorting algorithms preserve the relative order of equal elements, while unstable sorting algorithms don’t. 

## Sorting algorithm evaluation

We tested different sorting algorithms in order to discuss  about the fastest ones and to explain their main principles. We have implemented 6 different algorithms.

### Selection Sort

This algorithm selects the smallest element of a list in each iteration and places that element at the beginning of the list. 

```python
def selectionSort(tab):
    for i in range(len(tab)):
        min = i
        for j in range(i + 1, len(tab), 1):
            if tab[j] < tab[min]:
                min = j
        tab[i], tab[min] = tab[min], tab[i]
    return tab
```

| *Selection Sort Complexity* |        |
|-----------------------------|--------|
| Time Complexity             |        |
| Best                        | O(n²)  |
| Worst                       | O(n²)  |
| Average                     | O(n²)  |
| **Space Complexity**        | O(1)   |
| **Stability**               | No     |

### Insertion Sort

For this algorithm, we assume that the first element is already sorted, then we take another element and we compare it to the first one. If it’s greater than the sorted element we place it to the right, otherwise, to the left.

```python
def insertionSort(tab):
    for i in range(1, len(tab), 1):
        j = i
        while j > 0:
            if tab[j] >= tab[j - 1]:
                tab[j], tab[j - 1] = tab[j - 1], tab[j]
                j -= 1
            else:
                break
    return tab
```

| *Insertion Sort Complexity* |        |
|-----------------------------|--------|
| Time Complexity             |        |
| Best                        | O(n)   |
| Worst                       | O(n²)  |
| Average                     | O(n²)  |
| **Space Complexity**        | O(1)   |
| **Stability**               | Yes    |

### Bubble Sort

This algorithm compares two adjacent elements and swaps them until the list is sorted.

```python
#!/usr/bin/python
def bubbleSort(tab):
    for i in range(len(tab) - 1):
        for j in range(0, len(tab) - i - 1):
            if tab[j] > tab[j + 1] :
                tab[j], tab[j + 1] = tab[j + 1], tab[j]
    return tab
```

| *Bubble Sort Complexity*    |        |
|-----------------------------|--------|
| Time Complexity             |        |
| Best                        | O(n)   |
| Worst                       | O(n²)  |
| Average                     | O(n²)  |
| **Space Complexity**        | O(1)   |
| **Stability**               | Yes    |

## Quick Sort

For this one we will divide the list by using a pivot element. This pivot element should always be positioned in a way that elements to the left are smaller than the pivot and elements to the right are bigger than the pivot. We obtained sublists and those sublists are also divided until we have sublists of one element. After that we can recombine sublists into one.

```python
def partition(tab):
    l = []
    r = []
    for i in range(1, len(tab), 1):
        l.append(tab[i]) if tab[i] >= tab[0] else r.append(tab[i])
    return tab, l, r

def quickSort(tab):
    if len(tab) <= 1:
        return tab
    tab, left, right = partition(tab)
    sortLeft = quickSort(left)
    sortRight = quickSort(right)
    tab = sortLeft[0] + [tab[0]] + sortRight[0]
    return tab
```

| *Quicksort Sort Complexity* |               |
|-----------------------------|---------------|
| Time Complexity             |               |
| Best                        | O(n*log n)    |
| Worst                       | O(n²)         |
| Average                     | O(n*log n)    |
| **Space Complexity**        | O(log n)      |
| **Stability**               | No            |

### Merge Sort

This algorithm looks like the quick sort. We divide the list into sublists by cutting it in halves. When we have lists of one element we recombine the lists into greater sorted lists until we finished to recombine all lists.

```python
def mergeSort(tab):
    if len(tab) > 1:
        middle = len(tab) // 2
        left = tab[:middle]
        right = tab[middle:]
        tab = mergeSort(left)
        tab = mergeSort(right)
        i = 0
        j = 0
        k = 0
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                tab[k] = left[i]
                i += 1
            else:
                tab[k] = right[j]
                j += 1
            k += 1
        while i < len(left):
            tab[k] = left[i]
            i += 1
            k += 1
        while j < len(right):
            tab[k] = right[j]
            j += 1
            k += 1
    return tab
```

| *Merge Sort Complexity*     |               |
|-----------------------------|---------------|
| Time Complexity             |               |
| Best                        | O(n*log n)    |
| Worst                       | O(n*log n)    |
| Average                     | O(n*log n)    |
| **Space Complexity**        | O(n)          |
| **Stability**               | Yes           |

### Shell Sort

It’s a generalized version of the insertion sort we saw earlier. It sorts groups of elements that are far away from each other. The [idea][11] is to arrange the list of elements so that, starting anywhere, taking every hth element produces a sorted list --- such a list is said to be h-sorted. 

```python
def shellSort(n, array):
    interval = n // 2
    while interval > 0:
        for i in range(interval, n):
            temp = array[i]
            j = i
            while j >= interval and array[j - interval] > temp:
                array[j] = array[j - interval]
                j -= interval
            array[j] = temp
        interval //= 2
    return array
```

| *Shell Sort Complexity*     |               |
|-----------------------------|---------------|
| Time Complexity             |               |
| Best                        | O(nlog n)     |
| Worst                       | O(n²)         |
| Average                     | O(nlog n)     |
| **Space Complexity**        | O(1)          |
| **Stability**               | No            |


## Evaluation 

For this experiment we use python for testing the algorithms. We take a list of 5 000 numbers and try to sort them 10 times to see their stability and make a mean of the time it takes to sort (the list is always the same and the order of elements isn’t changed between each test). 

The PC used has an Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz   2.21 GHz processor and 16Go of ram. Since the time can be influenced by the processor's efficiency, time can change between other computers. Moreover, the algorithms used can probably be improved and the number of tests (only 10 by algorithms) could be increased to have a better idea of the time taken. 

## Results 

We noted the average time of each algorithm in seconds: 

- Selection Sort upon 10 sort of 5 000 elements: 1,313 seconds 
- Insertion Sort upon 10 sort of 5 000 elements: 1,727 seconds 
- Bubble Sort upon 10 sort of 5 000 elements: 2,42 seconds 
- Quick Sort upon 10 sort of 5 000 elements: 0,078 seconds 
- Merge Sort upon 10 sort of 5 000 elements: 0,078 seconds 
- Shell Sort upon 10 sort of 5 000 elements: 0,099 seconds 

## Références
- [https://github.com/CubeLeopard5/Sorting-Algrithms][1]
- [https://www.programiz.com/dsa/merge-sort][2]
- [https://www.programiz.com/dsa/quick-sort][3]
- [https://www.programiz.com/dsa/bubble-sort][4]
- [https://www.programiz.com/dsa/selection-sort][5]
- [https://www.programiz.com/dsa/insertion-sort][6]
- [https://www.programiz.com/dsa/shell-sort][7]
- [https://betterexplained.com/articles/sorting-algorithms/][8]
- [http://lwh.free.fr/pages/algo/tri/tri.htm][9]
- [https://www.jesuisundev.com/comprendre-les-algorithmes-de-tri-en-7-minutes/][10]

[1]: https://github.com/CubeLeopard5/Sorting-Algrithms 
[2]: https://www.programiz.com/dsa/merge-sort 
[3]: https://www.programiz.com/dsa/quick-sort 
[4]: https://www.programiz.com/dsa/bubble-sort 
[5]: https://www.programiz.com/dsa/selection-sort 
[6]: https://www.programiz.com/dsa/insertion-sort 
[7]: https://www.programiz.com/dsa/shell-sort 
[8]: https://betterexplained.com/articles/sorting-algorithms/ 
[9]: http://lwh.free.fr/pages/algo/tri/tri.htm 
[10]: https://www.jesuisundev.com/comprendre-les-algorithmes-de-tri-en-7-minutes/ 
[11]: https://en.wikipedia.org/wiki/Shellsort