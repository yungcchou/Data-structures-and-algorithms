# Linked List

A **Linked List** is a linear data structure that consists of a sequence of elements called **nodes**. Each node contains two parts:

1. **Data**: Stores the value or content of the node.
2. **Pointer/Link**: Stores the reference (or address) to the next node in the sequence.

Linked lists are different from arrays in that they do not store elements contiguously in memory. Instead, each element points to the next, making it easier to insert and delete nodes without rearranging other elements.

## Types of Linked Lists

1. **Singly Linked List**:

   - Each node contains data and a pointer to the next node.
   - Allows traversal in one direction only (forward).
   - Common operations include adding a node at the beginning, end, or at a specific position.

2. **Doubly Linked List**:
   - Each node contains data, a pointer to the next node, and a pointer to the previous node.
   - Allows traversal in both directions (forward and backward).
   - Provides more flexibility in manipulation but requires more memory for the extra pointer.

3. **Circular Linked List**:
   - The last node points back to the first node, forming a circular structure.
   - Can be singly or doubly linked.
   - Useful in applications requiring a circular traversal, such as round-robin scheduling.

## Advantages of Linked Lists

- **Dynamic Size**: Linked lists can grow or shrink in size without requiring memory reallocation.
- **Efficient Insertions/Deletions**: Adding or removing elements is more efficient than arrays, especially when performed at the beginning or end.

## Disadvantages of Linked Lists

- **No Random Access**: Linked lists do not support direct access to elements by index, making operations like searching slower (O(n) time complexity).
- **Extra Memory**: Each node requires extra memory for storing the pointer(s).

## Basic Operations in a Linked List

1. **Insertion**: Adding a new node at the beginning, end, or a specific position.
2. **Deletion**: Removing a node from a specific position or by key.
3. **Traversal**: Visiting each node from the head to the last node in sequence.
4. **Searching**: Finding a node containing a specific value by traversing the list.
5. **Deletion**: Deletes an element at the given index.
6. **Update**: Updates an element at the given index.

## Implement Linked List using Python class

- Node class contains data value and next node attributes
- LinkedList class contains a head node attribute and following functions
  - **`append( val )`**: add new node data to the end of linked list
  - **`getSize( )`**: get the total elements in the linked list
  - **`showAll( )`**: show the elements in the list from the first one to the last one, the symbol `->` is stayed between two node elements
  - **`insert( idx, val )`**: to insert new node after `idx`’s node, if success return True, otherwise return False
  - **`index( val )`**: return the index of the first found node which data value equals to input `val`, if not found then return `-1`
  - **`delete( val )`**: remove the first found node value equal to the input `val`, if there has no node data value equal to val then return `-1`
  - **`search( val )`**: return all of the `val` located node indexes in list. If not found, return `-1`