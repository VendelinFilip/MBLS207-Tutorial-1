## Page 1

Simulating evolution
MBLS-207 - Bioinformatics

# 1 Setup

In this tutorial, you will simulate a simple model of evolution to introduce you with concepts from bioinformatics using a (Jupyter) notebook. This model will describe mutating DNA sequences, but we simplify what mutations occur and how they occur. But first, we need to set up the stage. Imagine a DNA sequence that has evolved over time, accumulating mutations, and thus diverging into two different sequences. Let's think about how to compare these sequences now.

## Exercise 1

Open a new notebook. Define a function that takes two sequences as input and compares how identical they are. On what percentage of indices do they have matching entries? Assume that your inputs are of equal length.

## Exercise 2

One of the simplifications we will use is that we will always use sequences of the same length. Why is this a simplification?

## Exercise 3

Next, define another function that will mutate a given DNA sequence. The input is a DNA sequence, and the function randomly selects one of the bases, and mutates it. The DNA sequence with the mutation is returned. Python's `random` package comes in handy for this function.

