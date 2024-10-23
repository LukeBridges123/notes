# Comparison-Based Sorting
First we consider sorting algorithms that only use direct comparisons between elements; these work for any ordered data types. (We say this in order to distinguish them from algorithms like counting sort, which use special properties of the types of elements being sorted in order to sort them without direct comparisons.)
## Quadratic-Time Algorithms
### Selection Sort
In selection sort, we first loop over all $n$ elements to find the smallest, and place it at the start of the array; then, loop over the last $n-1$ elements to find the second smallest; and so on. This takes, say, $n$ comparisons on the first loop, $n-1$ on the second, and so on, for a total of $n + (n-1) + \dots + 2 + 1 = \frac{n(n-1)}{2}$ comparisons; thus it takes $O(n^2)$ steps in the worst case, and indeed in every case. This bad asymptotic behavior, combined with insensitivity to the properties of the input (cf. insertion sort. below, which has the same worst case but can do much better for almost-sorted inputs), makes it unsuitable for most purposes. The only useful property it has is that it minimizes the number of swaps needed, to about $n$, since it only does at most one swap per iteration (when placing the next-least element in its correct place); thus, in cases where swaps are much more expensive than other operations like accesses and comparisons, selection sort can beat other algorithms.
```
def selection_sort(arr):
	for i in range(len(arr)):
		current_min = arr[i]
		min_index = i
		for j in range(i, len(arr)):
			if arr[j] < current_min:
				current_min = arr[j]
				min_index = j
		arr[i], arr[min_index] = arr[min_index], arr[i]
	return arr
```
### Insertion Sort
Insertion sort proceeds as follows. First, look at the second element; if it is greater than the first, leave it where it is; otherwise, swap the two. Then, look at the third; if it is less than the second, swap it with the second; if it is less than the first as well, swap it with that too. After this, the first 3 elements will be sorted with respect to each other, though not necessarily in their final places. In general, on any given step the first $j$ elements of the array will be in sorted order; we then take the element at position $j+1$, and move it backwards (swapping with the element immediately before it) until it's greater than the element immediately before it. At that point, we know that all the elements before it are less than it, all the elements before it are greater than it, and more generally the whole first $j+1$ elements will be in sorted order. If we continue like this for $n$ iterations, the whole list will end up sorted.
```
def insertion_sort(arr):
	for i in range(1, len(arr)):
		j = i
		while j > 0 and arr[j] < arr[j-1]:
			arr[j-1], arr[j] = arr[j], arr[j-1]
			j -= 1
	return arr
```
#### Best vs. Worst Case
The worst case for insertion sort happens when the list is in reverse order. This means that element $j+1$ is less than all of the elements before it, so when we handle it, we have to put it at the start of the sorted sublist, which takes $j+1$ swaps. This means we need $1 + 2 + \dots + j + \dots + n$ swaps, or $O(n^2)$. 

On the other hand, when the list is already sorted, we don't have to do any swaps at all. At each step, we notice that the $j+1$ element is already greater than the $j$ element, hence the first $j+1$ elements are already in sorted order, and so we can move onto the next iteration. We still have to do $O(n)$ comparisons, for $O(n)$ steps total. This sort of reasoning generalizes to cases where the list is "almost sorted", with only a few elements out of order. If we assume, for instance, that the number of elements out of order is some fixed number $C$ independent of $n$, then insertion sort will only take $O(Cn) = O(n)$ steps. Thus, if a list is "almost sorted", insertion sort can often beat asymptotically faster algorithms like quicksort. Empirically, insertion sort often does better on small lists ($n < 5$, say) than the standard $O(n\log(n))$ algorithms, so those $n\log(n)$ algorithms can often be sped up by turning them into "hybrid sorts": on the recursive step (where you would ordinarily call, say, mergesort on a smaller sublist), call insertion sort instead if the sublist is small enough.
### Bubble Sort
## O(nlog(n)) Algorithms

### Mergesort
Mergesort is a recursive sorting algorithm, which works as follows: given an array of $n$ elements, divide it in half, and sort the two halves (typically by recursively calling mergesort); then merge the two sorted sublists: look at the first element of each sublist, choose the least of the two, and have that be the first element of the overall list; then look at the first remaining element of each sublist, and pick the least to be the second; and so on. (For example, we can merge $[1, 4, 8]$ and $[2, 3, 7]$ to get $[1, 2, 3, 4, 7, 8]$.)

The runtime $T(n)$ of mergesort follows the recurrence $T(n) = 2T(n/2) + O(n)$: recursively sorting the sublists takes 2 function calls which use $n/2$ operations each, and merging takes $O(n)$ operations; we can then solve the recurrence to get a runtime of $O(n\log(n))$. Alternatively, note that we'll have $O(\log(n))$ "levels" of the recursion, corresponding to the approximately $\log_2(n)$ times we need to cut a length-$n$ list in half before we get to single-element sublists; at each of those "levels", we do an $O(n)$ amount of work; this means an $O(n\log(n))$ amount of work total. Note that this is the same in the best and worst case.

There also exist bottom-up, iterative versions of mergesort, in addition to the top-down, recursive version described above. For example, we could maintain a queue of subarrays, which starts out filled with, for each element of the array, a 1-element array containing that element. We then repeatedly take two subarrays from the front of the queue, merge them, and push the result to the back, until we have only one element in the queue, which will be the complete sorted array. 
```
def merge(arr1, arr2):
	
```
### Quicksort
Quicksort follows a recursive strategy somewhat similar to that of mergesort. First, pick a "pivot"--an element of the array which is, hopefully, around the median of the elements. Then, *partition* the array, rearranging the elements so that everything less than the pivot is to the left of it, and everything greater than the pivot is to the right of it. The pivot is now in its final sorted position, and we just need to recursively sort the subarrays to its left and right.

A brief note on how partitioning can be done efficiently: ......
#### Pivot Selection and the Complexity of Quicksort
The asymptotic complexity of quicksort depends to some extent on how the pivot is selected. Its worst-case complexity is $O(n^2)$, which can happen if, for example, the chosen pivot always ends up being the least element of a given subarray. In that case, after partitioning the whole $n$-element array, an $O(n)$ operation no matter what, the pivot is in sorted order (as the least element, it will be in the leftmost position of the array), and we recur on an $n-1$ element subarray. If our pivot selection here is similarly bad, we'll then recur on an $n-2$ element subarray, and so on, ending up doing about $n + (n-1) + \dots + 1 = O(n^2)$ operations. 

This worst-case behavior can show up even in simple, common cases like an already-sorted array, if a naive pivot-selection rule (like just choosing the leftmost element of the subarray) is used.

Now consider what happens if we manage to choose the median as the pivot every time. In that case we just need to do a partition ($O(n)$ steps), followed by sorting two subarrays of size $n/2$. Thus, if quicksort takes $T(n)$ steps in the best case, then $T(n) = 2T(n/2) + O(n)$; this is the same recurrence that showed up when analyzing mergesort, and solving it shows that quicksort takes $O(n\log(n))$ if we choose our pivots like this. 

A simple heuristic that can help us achieve $O(n\log(n))$ runtime is the "median-of-three" rule: take the first, last, and middle elements of the array, and let the median of those three be the pivot. This still has an $O(n^2)$ worst-case runtime, but no longer fails on common cases like a sorted array, and works reasonably well empirically.

A more sophisticated strategy is to choose the pivot randomly. For some intuition on why this might work, label the elements by how they would be ordered when sorted (so 1 corresponds to the least element, 2 is the second least, and so on, up to the greatest element $n$.) If we choose an element at random, the expected label is $n/2$, i.e. we expect to get an element near the median. Now consider a run of quicksort where you pick each pivot at random. Some will be "bad" (far from the median), some will be "good" (close to the median), but *on average* they'll be near the median, by the argument above. Thus we expect (in the colloquial sense and the mathematical sense) that we'll only need to perform $O(n\log(n))$ steps on average, as would be the case if we always chose an optimal pivot. 
### Heapsort
Recall that we can turn an $n$-element list into a min heap in only $O(n)$ steps (the "heapify" algorithm). We can therefore sort a list by heapifying it and then repeatedly removing the minimum element of the heap, which we then push to the end of an array. Each removal operation takes $O(\log(n))$ steps, so building a sorted list from the heap takes $O(n\log(n))$ steps, for a total runtime of $O(n\log(n)) + O(n) = O(n\log(n))$ steps to sort an array this way. 
## Optimality of O(nlog(n)) Algorithms
No comparison-based sorting algorithm can have a worst-case runtime faster than $O(n\log(n))$. 

To see this, we first reframe the task of sorting an array in terms of permutations. An unsorted array of (without loss of generality, distinct) elements is a permutation of the (unique) sorted array with the same elements; in order to sort, we have to figure out which permutation we have. (A bit of bookkeeping where we make note of where each element starts and where it ends up after we sort allows us to find this explicitly by sorting.) There are $n!$ possible permutations, so it takes $O(\log(n!))$ bits to specify each permutation. Each comparison we make gives us at most 1 bit of information about which permutation we have, so we expect that it will take at least $O(\log(n!))$ comparisons to sort a list. By Stirling's approximation, $n! \approx (n/e)^n$, so $\log(n!) \approx \log((n/e)^n) = n\log(n/e) = n\log(n) - n\log(e)$ which is $O(n\log(n))$. Thus it ought to take at least $O(n\log(n))$ comparisons to sort a list in the worst case; mergesort and heapsort, among others, achieve this bound. 
# Non-Comparison-Based Sorting
When the objects being sorted have certain special properties, we can use non-comparison-based algorithms that can beat the $O(n\log(n))$ bound on comparison-based sorting, getting as low as $O(n)$. 
## Counting Sort
Suppose that there are only $k$ different kinds objects in our array--without much loss of generality, we can just say the integers $1, \dots, k$--and we know in advance which $k$ we'll have to deal with. Then we can sort with the following procedure: go through all elements of the array, keeping track of the number $N_i$ of copies of element $i$. Then fill the first $N_1$ spaces in the array with $1$, the next $N_2$ with $2$, and so on. This takes $O(n+k)$ time; often we will have $k = O(n)$ (if, for instance, our arrays of size $n$ will only hold copies of the integers $1$ through $n$) or even $k = O(1)$, in which case this reduces to $O(n)$ time. 

## Radix Sort
