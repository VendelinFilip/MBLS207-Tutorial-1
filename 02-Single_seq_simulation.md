# 2 Simulating the evolution of a single sequence

We now have the basis of our model: the ability to mutate sequences. Next, we are going to simulate evolution by taking a sequence and letting it mutate in a number of time steps. Then, we are going to compare how identical the mutating sequence is with the original sequence.

&lt;page_number&gt;1&lt;/page_number&gt;

---


## Page 2

**Exercise 4**

In a new cell, generate a (random) DNA sequence of 50 nucleotides. Then, write a loop that will 1) mutate the sequence and 2) compare the mutated sequence with the original sequence and 3) store the identity scores in a list, for 600 time/mutation steps

**Exercise 5**

Now we have a list with similarity scores over a series of time/mutation steps. Make a plot of these data to show similarity scores as a function of time/mutation steps.

**Exercise 6**

What do you notice on the similarity score over time? Can you explain this?

**Exercise 7**

What will this plot look like if instead of comparing the original sequence with mutated versions of itself, we compare the original sequence with a mutating sequence that initially has no base in common with the original sequence, like the complementary sequence?

**Exercise 8**

What is the effect of the sequence length? Compare the identity scores over time of a short and long sequence.


