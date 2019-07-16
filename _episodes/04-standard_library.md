---
title: "The Python Standard Library"
teaching: 60
exercises: 60
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## The Notebook

The material for this episode is on this notebook:

~~~
WVU Research Computing (03. Python Standard Library).ipynb
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


{% include links.md %}
