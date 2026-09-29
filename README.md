# Huffman Coding Compression Engine (Java)

A custom, low-level implementation of the **Huffman Coding Algorithm** in Java. This project demonstrates lossless data compression by building a variable-length prefix code based on symbol frequencies using custom-built binary tree (`BinNode`) and linked list (`Node`) data structures.

---

## Technical Overview

The application compresses plain text by assigning shorter bit sequences to frequently occurring characters and longer sequences to rarer ones. This implementation builds its own priority queue and tree infrastructure from scratch to handle symbol frequency analysis, greedy binary tree assembly, and recursive code generation.

---

## Core Architecture & Components

* **`Encoder.java`**: Handles text parsing, frequency mapping, tree building, and bitstream encoding.
* **`BinNode<T>`**: Generic binary tree node structure used to build the Huffman coding tree (`BinNode<CountSymbol>`).
* **`Node<T>`**: Custom singly-linked list node used to maintain a sorted queue of tree nodes ordered by symbol frequency.
* **`CountSymbol`**: Pair data structure binding a character (`char`) with its occurrence count (`int`).
* **`Decoder.java`**: Traverses the constructed Huffman tree using bit patterns to reconstruct original strings.

---

## Algorithmic Workflow

1. **Frequency Analysis (`buildCountQueue`):**
   * Scans input text and accumulates ASCII symbol counts using an index-mapped frequency table ($128$-element ASCII array).
   * Constructs leaf nodes for each active symbol and inserts them into a custom-sorted linked list.

2. **Greedy Huffman Tree Construction (`buildTree`):**
   * Repeatedly extracts the two lowest-frequency nodes from the sorted list.
   * Merges them under a new parent node whose frequency is the sum of its children.
   * Re-inserts the parent node back into the sorted linked list until a single root tree remains.

3. **Prefix Code Generation (`encodeChar`):**
   * Recursively traverses `symbolTree` from root to leaf to dynamically generate binary path representations (`0` for left branches, `1` for right branches).

4. **Bitstream Encoding (`encode`):**
   * Maps each input character to its variable-length binary string representation to generate the full compressed output stream.

---

## Complexity Analysis

| Phase | Time Complexity | Space Complexity | Notes |
| :--- | :--- | :--- | :--- |
| **Frequency Count** | $\mathcal{O}(N)$ | $\mathcal{O}(1)$ | Fixed $128$-ASCII table allocation; $N$ = string length |
| **Sorted List Insertion** | $\mathcal{O}(K^2)$ | $\mathcal{O}(K)$ | Insertion sort over $K$ unique characters |
| **Tree Construction** | $\mathcal{O}(K^2)$ | $\mathcal{O}(K)$ | Merges $K$ leaf nodes into a single binary tree |
| **Encoding Traversal** | $\mathcal{O}(N \cdot H)$ | $\mathcal{O}(H)$ | $H$ = height of Huffman tree |

---

## Tech Stack

* **Language:** Java (JDK 8+)
* **Data Structures:** Binary Trees (`BinNode`), Custom Linked Lists (`Node`), Frequency Maps
* **Concepts:** Lossless Data Compression, Greedy Algorithms, Dynamic Code Generation, Recursion
