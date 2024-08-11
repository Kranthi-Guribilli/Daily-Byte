
## Algorithms
**Sorting**

* **Quick Sort**
  * Stable: ```No```
  * Time Complexity:
    * Best case: ```O(nlog(n))```
    * Worst case: ```O(n^2)```
    * Average case: ```O(nlong(n))```
  <img src ="https://github.com/Kranthi-Guribilli/Daily-Byte/blob/main/images/quicksort.gif" />

* **Merge Sort**
  * It is also a divide and conquer algorithm. It continuously divides an array into two halves, recurses on both the left subarray and right subarray and then meges the two sorted halves
  * Stable: ```Yes```
  * Best case: ```O(nlog(n))```
  * Worst case: ```O(nlog(n))```
  * Average case: ```O(nlog(n))```
  <img src ="https://github.com/Kranthi-Guribilli/Daily-Byte/blob/main/images/mergesort.gif" />

* **Bucket Sort**
  * Bucket Sort is a sorting algorithm that works by distributing the elements of an array into a number of buckets. Each bucket is then sorted individually, either using a dofferent sorting algorithm, or by recursively applying the bucket sorting algorithm
  * Time Complexity:
    * Best case: ```Ω(n + k)```
    * Worst case: ```O(n^2)```
    * Average case: ```Θ(n + k)```
  <img src ="https://github.com/Kranthi-Guribilli/Daily-Byte/blob/main/images/bucketsort.png"/>

* **Radix Sort:**
  * Radix Sort is a sorting algortihm that like bucket sort, distributes elements of an array into a number of buckets. However, radix sirt differs from bucket sort by 're-bucketing' the array after the intial pass as opposed to sorting each bucket and merging
  * Time Complexity:
    * Best case: ```Ω(nk)```
    * Worst case: ```O(nk)```
    * Average case: ```Θ(nk)```
      
