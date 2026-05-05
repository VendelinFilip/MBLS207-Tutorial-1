# Solutions to the Exercises

## Solution 1

```python
def seq_identity(seq1, seq2):
    return (100*sum([a==b for a,b in zip(seq1, seq2)])/len(seq1))

def seq_identity(seq1, seq2):
    id_elements=0
    for n in range(len(seq1)):
        if seq1[n]==seq2[n]:
            id_elements+=1
    return (100*id_elements/len(seq1))
```

## Solution 2

In reality, we also have insertions and deletions as possible mutations, which cannot occur if sequences must remain the same length.

## Solution 3

```python
import random
def mutate(seq):
    bases=['A', 'T', 'C','G']
    random_index=random.choice(range(len(seq)))
    bases.remove(seq[random_index])
    new_base=random.choice(bases)
    new_seq=seq[0:random_index]+new_base+seq[random_index+1:]
    return(new_seq)
```

## Solution 4

```python
original_seq=''.join(random.choices(['A', 'T', 'C','G'],k=50))
identity_scores=[100]
mutated_seq=original_seq
for time in range(1000):
    mutated_seq=mutate(mutated_seq)
    identity_scores.append(seq_identity(original_seq,mutated_seq))
```

## Solution 5

```python
import matplotlib.pyplot as plt
plt.plot(range(len(identity_scores)), identity_scores)
plt.xlabel('Time steps')
plt.ylabel("% Identity")
plt.ylim(0,100)
plt.xlim(0, len(identity_scores))
```

## Solution 6

The similarity score rapidly decreases in the first time steps, but after a while seems to stagnate around 25%. This 25% is the expected identity between two randomly drawn sequences.

## Solution 7

Since we start out with no similarities between the two sequences, and mutation will introduce similarities, the identity score will increase over time towards 25%.

## Solution 8

With longer sequences, the decrease in identity score is slower than with shorter sequences.

## Solution 9

Looking up from MBLS102:

```python
def translate_dna(dna_seq):
    bases = ["T", "C", "A", "G"]
    codons = [a+b+c for a in bases for b in bases for c in bases]
    amino_acids = "FFLLSSSSYY**CC*WLLLLPPPPHHQQRRRRIIIMTTTTNNKKSSRRVVVVAAAADDEEGGGG"
    codon_table = dict(zip(codons, amino_acids))
    protein_seq = []
    for i in range(0, len(dna_seq), 3):
        codon = dna_seq[i:i+3]
        if codon in codon_table:
            protein_seq += codon_table[codon]
        else:
            protein_seq += "u"
    return ''.join(protein_seq)
```

## Solution 10

```python
original_seq=''.join(random.choices(['A','T','C','G'],k=500))
original_aa_seq=translate_dna(original_seq)
identity_scores=[100]
identity_scores_aa=[100]
mutated_seq=original_seq
for time in range(1000):
    mutated_seq=mutate(mutated_seq)
    identity_scores.append(seq_identity(original_seq,mutated_seq))
    identity_scores_aa.append(seq_identity(original_aa_seq,translate_dna(mutated_seq)))
```

## Solution 11

The identity between protein sequences saturate to a lower level, corresponding to the higher number of amino acids, and hence lower expected identity between two random protein sequences.

## Solution 12

When we only allow true mutations, we know that each time step in our simulation a mutation will occur. In the case where we also allow a substitution with the original base, we have 25% of not having an actual mutation. So, in the same number of steps, the second option will have only had 75% actual mutations. In other words, in the same amount of steps, we perceived fewer mutations, or evolution goes slower.

## Solution 13

The original sequence can be seen as an ancestral sequence. Instead, looking at two independently mutation sequences doesn't change the outcome much: if we only let one of the two mutate in every single time step, the results are the same. If both of them can mutate in the same step, that's equivalent to having time run twice as quickly.

## Solution 14

Many, to name the most important ones:
* The exclusion of evolutionary pressure to keep certain bases/amino acids the same.
* Mutation rates, this model doesn't explicitly model time but mutation steps. Mutation rates (number of mutations per time unit) can differ between species.
