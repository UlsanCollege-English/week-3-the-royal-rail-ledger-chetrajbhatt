# README Starter Template

# Week 3: The Royal Rail Ledger

## Summary
This assignment focuses on linked-list operations in a railway story setting. I implemented functions for building and reading a singly linked list, finding the first repeated value, removing banned cargo from a doubly linked list, and checking whether a train is a palindrome. The assignment uses both singly linked lists and doubly linked lists. The hardest part was ensuring that both the `head` and `tail` pointers of the doubly linked list were updated correctly when multiple consecutive target nodes were removed from the edges.

---

## Approach
### `build_sll_from_list(values)`
- I started with checking if the values list was empty, returning an empty `SinglyLinkedList` if so.
- I built the list by setting the first element as `sll.head` and keeping track of the current node using a pointer.
- I made sure the values stayed in the correct order by iterating forward through the rest of the values array, attaching new nodes to `current.next` and advancing the pointer.

### `sll_to_list(sll)`
- I started at the `sll.head` of the singly linked list.
- I traversed the list by using a `while current is not None:` loop, moving forward with `current = current.next`.
- I collected values in a Python list by appending `current.value` to an accumulator list during each loop iteration.

### `find_first_repeat_sll(sll)`
- I tracked values I had already seen by storing them in a Python `set()`, which allows for $O(1)$ lookup times.
- When I found a repeated value (using an `in` check on the set), I immediately returned that value to guarantee it was the first repeated instance from left to right.
- If I reached the end with no repeat, I returned `None`.

### `remove_all_from_dll(dll, target)`
- I traversed the list using a `while` loop starting from `dll.head` down to the end of the list.
- When I found the target value, I updated the neighboring nodes' references (`prev.next` and `next.prev`) to bridge the gap and skip the deleted node.
- I checked special cases such as when the target was at the `dll.head` (shifting head forward) or at the `dll.tail` (shifting tail backward).

### `is_train_palindrome(dll)`
- I compared values from both ends of the list simultaneously using a `left` pointer at `dll.head` and a `right` pointer at `dll.tail`.
- I stopped when the `left` and `right` pointers met in the middle or bypassed each other.
- I returned `True` or `False` based on whether all symmetrically opposed node values matched exactly.

---

## Complexity

### `build_sll_from_list(values)`
- **Time complexity:** $O(n)$
- **Space complexity:** $O(n)$
- **Why:** We iterate through the python list of size $n$ exactly once, allocating a new `SLLNode` for every single element, which scales linearly with input size.

### `sll_to_list(sll)`
- **Time complexity:** $O(n)$
- **Space complexity:** $O(n)$
- **Why:** We must traverse all $n$ nodes in the linked list sequentially, and the resulting Python array stores all $n$ collected elements.

### `find_first_repeat_sll(sll)`
- **Time complexity:** $O(n)$
- **Space complexity:** $O(n)$
- **Why:** In the worst-case scenario (no duplicates), we visit all $n$ elements once. The lookup set also grows to hold up to $n$ unique values in memory.

### `remove_all_from_dll(dll, target)`
- **Time complexity:** $O(n)$
- **Space complexity:** $O(1)$
- **Why:** We perform a single loop through the entire list of $n$ elements to find matches. Node deletions happen in-place by altering existing pointers without allocating new memory blocks.

### `is_train_palindrome(dll)` *(stretch)*
- **Time complexity:** $O(n)$
- **Space complexity:** $O(1)$
- **Why:** The two pointers move inward toward each other, visiting at most $n/2$ nodes, which simplifies to linear time. No extra collections or copies are created.

---

## Edge-Case Checklist
Mark each item after you test it.

- [x] empty SLL
- [x] empty DLL
- [x] single-node SLL
- [x] single-node DLL
- [x] no repeated values in SLL
- [x] repeated value appears later in SLL
- [x] repeated value includes the head value
- [x] removing from DLL when target is at head
- [x] removing from DLL when target is at tail
- [x] removing consecutive target values in DLL
- [x] removing all nodes from DLL
- [x] palindrome with odd length
- [x] palindrome with even length
- [x] non-palindrome DLL

---

## Assistance & Sources

### AI use
- I used AI: Yes
- If yes, what did it help with? It helped me conceptualize the pointer rearrangement for removing nodes from a Doubly Linked List safely without breaking links, and helped fix terminal pathing configurations in VS Code.

### Other sources
- Class notes: Reviewed basic structure definitions for Singly vs Doubly linked nodes.
- Slides: Followed the visual pathing diagrams showing how `node.next` and `node.prev` linkages break and reconnect.

---

## Debugging Notes

- I first got stuck on `remove_all_from_dll` because I wasn't caching `current.next` before unlinking a node, causing the loop to lose track of the remaining list.
- The failing test that helped me most was removing sequential matching targets at the edges (like erasing `[5, 5, 1, 2]` where 5 is the target).
- I fixed the issue by separating head/tail updates from structural neighboring pointer re-assignments and updating a cached `next_node` variable at the top of the loop block.
- One mistake I will avoid next time is mutating or severing node linkages while simultaneously relying on those same links to move forward through a loop.

---

## Final Reflection
This assignment taught me that working with linked lists requires hyper-vigilance about pointer tracking, as one minor mistake can isolate portions of your data structures into memory leaks. Working with a Doubly Linked List was trickier because you have double the references (`prev` and `next`) to handle, but its ability to read backward makes tasks like checking for palindromes highly efficient without requiring extra data collections.