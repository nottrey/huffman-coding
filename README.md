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

## Tech Stack

* **Language:** Java (JDK 8+)
* **Data Structures:** Binary Trees (`BinNode`), Custom Linked Lists (`Node`), Frequency Maps
* **Concepts:** Lossless Data Compression, Greedy Algorithms, Dynamic Code Generation, Recursion
