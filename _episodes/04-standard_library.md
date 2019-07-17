---
title: "The Python Standard Library"
teaching: 60
exercises: 60
questions:
- "What is the Standard Library and which are the main modules for scientific computing"
objectives:
- "Understand the difference between the Standard Library and the Python Language itself"
keypoints:
- "Several modules in the standard library are often used in Scientific Computing"
---

## The Notebook

The material for this episode is on this notebook:

~~~
2_Python_Standard_Library [WVU Research Computing].ipynb
~~~
{: .source}

## Exercises

### Hyperbolic Sine

The hyperbolic sine function is defined as Sinh(z) = 0.5 (exp(z) - exp(-z))

    1. Using the `math`, on the reals, confirm evaluate the RHS and LHS independently for
    a list of 20 numbers from 0 to PI

    2. Now using `cmath` produce a similar confirmation for a line of values that is
    0.5 in the imaginary space.


### Exploring World Population

The file `population_data.json` is a JSON file with population data from 1960 up to 2000.

  1. Open the file using the `json` module from the Standard Library and recover a list of dictionaries.

  2. For each country or group of countries, collect the population in 1980 and the population in 2000. Computed the relative difference as a percentage of change.

  3. Which is the country with the highest growth in population between 1980 and 2000?

  4. Create a set of folders one for each country storing there the population values in a file as
  text file. You will realize that reading files from text files is actually harder than storing this kind of data in JSON files.


## Pharmaceutical Spending in countries

There is another dataset downloaded from <https://datahub.io/core/pharmaceutical-drug-spending#data>
and <https://datahub.io/>

The file was downloaded as `pharma_countries.json`

Read that JSON file and get the collection of spending data for USA.

## Rolling dices

Compute all the possible outcomes of rolling 3 dices using the itertools module.

## Multiprocessing

Use the multiprocessing for computing the different k-mers for several sizes.

This couple of functions can help, use them with the multiprocessing module to speed up the calculation.

~~~
import numpy as np

genome = "".join(random.choice("AGCT") for _ in range(1000))

def perfect_reads(genome, n_reads=10):
    """Create perfect reads from `genome`"""
    starts = np.random.randint(len(genome), size=n_reads)
    length = np.random.randint(27,33, size=n_reads)
    for n in range(n_reads):
        low = starts[n]
        yield genome[low:low + length[n]]

def kmers(read, k=10):
    """Generate `k`-mers from a `read`"""
    for n in range(len(read) - k + 1):
        yield read[n:n+k]

def get_perfect_kmers(genome):
    kmers_ = []
    for read in perfect_reads(genome, n_reads=1000):
        for kmer in kmers(read):
            kmers_.append(kmer)

    return kmers_    
~~~
{: .source}

Verify that not matter the size of the k-mers, most of them end up being duplicates.

~~~
kmers_ = get_perfect_kmers(genome)
# lots of kmers, but not that many are unique
print(len(kmers_), len(set(kmers_)))
~~~
{: .source}


{% include links.md %}
