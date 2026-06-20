# Week 3 Homework: The Royal Rail Ledger

![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)

Welcome to the Week 3 assignment for the Ulsan College English/Data Structures course. In this assignment, you will practice working with **Singly Linked Lists (SLL)** and **Doubly Linked Lists (DLL)** to manage the ledger of the "Royal Rail" train system.

---

## 📋 Objectives

Your task is to implement the missing logic for the following functions inside `ledger.py` (or your primary assignment script) using **Python's standard library only**:

1. **`build_sll_from_list(values: list[int]) -> SinglyLinkedList`**
   * Converts a standard Python list of integers into a custom Singly Linked List.
2. **`sll_to_list(sll: SinglyLinkedList) -> list[int]`**
   * Traverses a Singly Linked List and returns its values back as a standard Python list.
3. **`find_first_repeat_sll(sll: SinglyLinkedList) -> int | None`**
   * Iterates from left to right and returns the very first value that appears more than once.
4. **`remove_all_from_dll(dll: DoublyLinkedList, target: int) -> None`**
   * Traverses a Doubly Linked List and removes all nodes matching the target value, properly updating both `head` and `tail` pointers.
5. **`is_train_palindrome(dll: DoublyLinkedList) -> bool` (Stretch Goal)**
   * Checks if the train data reads the same forward and backward by leveraging two pointers meeting in the middle.

---

## 🛠️ Setup Instructions

To get started on your local machine, open your terminal and follow these steps:

1. **Clone your repository:**
   ```bash
   git clone [https://github.com/UlsanCollege-English/week-3-the-royal-rail-ledger-chetrajbhatt.git](https://github.com/UlsanCollege-English/week-3-the-royal-rail-ledger-chetrajbhatt.git)