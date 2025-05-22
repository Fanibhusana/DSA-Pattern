# Two Pointers Pattern in DSA (Java)

## 1. When to Use It

Use the Two Pointers technique when you need to:

- Process or analyze elements from both ends of a data structure (commonly arrays or linked lists).
- Solve problems involving finding pairs, triplets, or subarrays that satisfy certain conditions (like sums, differences).
- Optimize searching, sorting, or partitioning problems where a brute force approach might be `O(n^2)`.
- Work on sorted arrays or strings where you can leverage order to efficiently traverse the structure.

**Typical problems include:**
- Finding pairs/triplets with a given sum.
- Merging two sorted arrays.
- Removing duplicates or specific elements.
- Palindrome checking.
- Sliding window problems (a variation).

---

## 2. Core Idea & Algorithm 

The core idea is to use two pointers (indexes) to scan through the array or string simultaneously, but from different directions or with different speeds.

- Initialize one pointer at the start (`left`).
- Initialize another pointer at the end (`right`).
- Move pointers towards each other or sometimes in the same direction depending on the problem.
- At each step, compare or process the elements at these pointers.
- Adjust pointers based on conditions (e.g., increase left pointer, decrease right pointer).
- Stop when pointers meet or cross.

This avoids nested loops and reduces time complexity.

---

## 3. Java Template Code (Clean & Reusable)

Here is a clean and reusable Java template for the classic two-pointer scenario on a sorted array:

```java
public class TwoPointersTemplate {
    
    public static void twoPointersExample(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while (left < right) {
            // Example condition: sum of two pointers
            int sum = nums[left] + nums[right];

            if (sum == target) {
                // Found the target pair, process accordingly
                System.out.println("Pair found: (" + nums[left] + ", " + nums[right] + ")");
                // If need all pairs, move pointers accordingly:
                left++;
                right--;
            } else if (sum < target) {
                // Need larger sum, move left pointer right to increase sum
                left++;
            } else {
                // Need smaller sum, move right pointer left to decrease sum
                right--;
            }
        }
    }
}
```

**Key points:**
- Always initialize pointers carefully.
- Make sure to handle pointer movement based on conditions.
- The loop usually continues while `left < right` (or a similar condition).

---

## 4. Common Variations

- **Same-direction pointers:** Both pointers start at the beginning but move forward at different speeds (e.g., slow/fast pointers for cycle detection).
- **Fixed-size sliding window:** Two pointers maintain a window of size `k` or variable size to find subarrays.
- **Merging sorted arrays:** Two pointers run through two different arrays.
- **Removing duplicates or partitioning:** Left pointer tracks position to place new elements, right pointer scans through the array.
- **Palindrome checking:** One pointer at start, one at end, compare characters.

---

## 5. Time & Space Complexity

**Time Complexity:**  
Usually `O(n)` — Each pointer moves through the array at most once. Since the pointers move linearly and never go backwards, the total operations are proportional to `n`.

**Space Complexity:**  
`O(1)` — The algorithm uses only a constant amount of extra space for the pointers and temporary variables.

This efficiency is why the two-pointer pattern often replaces naive `O(n^2)` nested loops.

---

## 6. Common Mistakes/Pitfalls + Must-Solve LeetCode Problems

**Common Mistakes:**
- Not handling the pointer movement correctly, causing infinite loops.
- Forgetting to check boundary conditions like `left < right`.
- Misusing pointers on unsorted data where sorting is necessary.
- Overcomplicating the pointer update logic.
- Not considering duplicates when needed (e.g., skipping duplicates in pair finding).

**Must-Solve LeetCode Problems:**
- [Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
- [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
- [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
- [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
- [3Sum (advanced variation using two pointers)](https://leetcode.com/problems/3sum/)

---

## Bonus: Tips to Approach Two Pointer Problems Effectively

- Sort the array/string first if necessary to exploit ordering.
- Clearly define what each pointer represents (start/end, slow/fast).
- Work through a dry run with an example to understand how pointers move.
- Think about the loop condition carefully to avoid infinite loops.
- Use helper variables for sums, counts, or conditions to keep code clean.
- Practice by solving problems progressively from simple (two sum) to complex (3Sum, palindrome).
- Always clarify constraints — is input sorted? Are duplicates allowed?
