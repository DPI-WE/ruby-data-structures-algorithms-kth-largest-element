# Find the "Kth" Largest Element in an Array 🔍

## The problem
Write a function that:
- Takes an unsorted array of integers (array) and an integer (k).
- Finds the kth largest element in the sorted order, not the kth distinct element.
- Returns the kth largest element.

## Understand the Problem
Before we dive into the solution, let's ensure we understand the task with a simple exercise.

- Consider the array `[3, 2, 1, 5, 6, 4]` and `k = 2`. What is the 2nd largest element in this array?
- (3, 2)
  - Incorrect. This answer does not represent a single element, and neither of these numbers is the 2nd largest element in the array.
- 5
  - Correct! When the array is considered in sorted order `[1, 2, 3, 4, 5, 6]`, the 2nd largest element is indeed 5.
- 4
  - Incorrect. While 4 is an element in the array, it is not the 2nd largest element when the array is sorted.
{: .choose_best #understanding_the_problem title="What is the 2nd largest element in the array `[3, 2, 1, 5, 6, 4]`?" points="1" answer="2" }

This exercise helps to illustrate the concept of sorting and finding elements by their order in an array. Keep this understanding as we proceed to solve the main problem.

## Think Aloud
Express your thought process out loud. Begin with a brute force method, like sorting the array and finding the kth largest element by index. Discuss the efficiency of this approach and how it might be improved, perhaps with a heap or priority queue for better time complexity.

## Test your code

```ruby
arrays = [
  [3, 2, 1, 5, 6, 4],
  [3, 2, 3, 1, 2, 4, 5, 5, 6],
  [1, 2, 3, 4, 5, 6, 7, 8, 9]
]
ks = [2, 4, 5]
array = arrays.sample
k = ks.sample
# write your function here
def find_kth_largest(array, k)

end

puts find_kth_largest(array, k)
```
{: .repl #kth_largest_element title="Find the Kth Largest Element" readonly_lines="[1,2,3,4,5,6,7,8,9,11]"}

```ruby
describe "Find the Kth Largest Element" do
  it "finds the 2nd largest element in the array [3, 2, 1, 5, 6, 4]" do
    result = find_kth_largest([3, 2, 1, 5, 6, 4], 2)
    expect(result).to eq(5)
  end
end
```
{: .repl-test #kth_largest_element_test_1 for="kth_largest_element" title="Find the Kth Largest Element finds the 2nd largest" points="1"}

```ruby
describe "Find the Kth Largest Element" do
  it "finds the 4th largest element in the array [3, 2, 3, 1, 2, 4, 5, 5, 6]" do
    result = find_kth_largest([3, 2, 3, 1, 2, 4, 5, 5, 6], 4)
    expect(result).to eq(4)
  end
end
```
{: .repl-test #kth_largest_element_test_2 for="kth_largest_element" title="Find the Kth Largest Element finds the 4th largest" points="1"}

```ruby
describe "Find the Kth Largest Element" do
  it "finds the 5th largest element in the array [1, 2, 3, 4, 5, 6, 7, 8, 9]" do
    result = find_kth_largest([1, 2, 3, 4, 5, 6, 7, 8, 9], 5)
    expect(result).to eq(5)
  end
end
```
{: .repl-test #kth_largest_element_test_3 for="kth_largest_element" title="Find the Kth Largest Element finds the 5th largest" points="1"}

```ruby
describe "Find the Kth Largest Element" do
  it "handles a large array efficiently, suggesting O(n) time complexity" do
    large_array = Array.new(100000) { rand(-10000..10000) }
    k = rand(1..100)
    
    start_time = Time.now
    result = find_kth_largest(large_array, k)
    end_time = Time.now

    execution_time = end_time - start_time

    expect(execution_time).to be < 1 # Adjust this threshold based on expected performance
  end
end
```
{: .repl-test #kth_largest_element_test_4 for="kth_largest_element" title="Find the Kth Largest Element handles a large array efficiently, suggesting O(n) time complexity" points="1"}

## Tips and Clues for Solving the Problem
- **Sorting**: A simple approach is to sort the array in descending order and pick the kth element. This is intuitive but may not be the most efficient in terms of time complexity.
- **Heap**: A more sophisticated and efficient method involves using a priority queue or heap to keep track of the largest elements seen so far. Try initializing a heap (sorted array) of the first k elements in the array, then iterate through the remaining elements, adding any elements that are larger than the smallest in the heap.
- **Edge Cases**: Consider what happens if k is larger than the array size or if the array contains duplicates. How will your solution handle these cases?

## Quiz
- What is the time complexity of finding the kth largest element using sorting?
- O(n log n) due to the time complexity of sorting algorithms like quicksort or mergesort.
  - Correct! Sorting the array is a common approach, and most efficient sorting algorithms have a time complexity of O(n log n).
- O(n) if using a linear time selection algorithm or a properly implemented priority queue.
  - Correct, but with a nuance. While the average case for some selection algorithms or a heap can approach O(n), this is highly dependent on the implementation and the nature of the data.
- O(n^2) as it requires checking each element against every other element.
  - Incorrect. While some naive sorting algorithms have O(n^2) complexity, more efficient algorithms are typically used for this problem.
{: .choose_best #time_complexity title="What is the time complexity of finding the kth largest element using sorting?" points="1" answer="1" }

- Which data structure can optimize the process of finding the kth largest element?
- Array, when sorted.
  - Correct, but more efficient methods exist. Sorting the array does allow for finding the kth largest element, but sorting first might not be the most efficient approach.
- Priority Queue (Heap).
  - Correct! A priority queue or heap is especially useful for efficiently finding the kth largest element without needing to sort the entire array.
- Linked List.
  - Incorrect. While you can find the kth largest element by traversing a linked list, this method lacks the efficiency and benefits provided by a priority queue or sorting.
{: .choose_best #data_structure_optimization title="Which data structure can optimize the process of finding the kth largest element?" points="1" answer="2" }

- How does a heap help in finding the kth largest element?
- By allowing linear search through all elements.
  - Incorrect. Heaps do not facilitate linear search through elements; they structure data in a way that allows for efficient extraction of the maximum or minimum element.
- By organizing elements so that the kth largest can be found without sorting the entire array.
  - Correct! A heap, particularly a min-heap or max-heap, can be used to maintain a subset of the largest elements, allowing for efficient extraction of the kth largest element.
- By encrypting the array elements for secure comparison.
  - Incorrect. Heaps do not involve encryption; they are a data structure that organizes elements to allow for efficient access to the largest or smallest values.
{: .choose_best #heap_benefit title="How does a heap help in finding the kth largest element?" points="1" answer="2" }

## Conclusion
In this lesson, we've tackled the challenge of finding the kth largest element in an unsorted array. By exploring different approaches, including brute force sorting and more efficient heap-based methods, you've gained insight into algorithm design and optimization techniques crucial for software development and technical interviews.

## Resources
- [leetcode](https://leetcode.com/problems/kth-largest-element-in-an-array/)
