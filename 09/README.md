# Assignment 9

The goal of this assignment is to expand your knowledge on and familiarity with OpenMP.

## Exercise 1 (1.5 Points)

### Description

In this exercise, you are asked to investigate the effect of first touch in multi-threaded programs, as discussed in the lecture.

### Tasks

1) Open [first_touch/first_touch.c](first_touch/first_touch.c), familiarize yourself with the code and parallelize it using OpenMP.
2) How can you control the mapping of threads to cores? Modify the program such that you are using 12 threads, each one fixed to a single physical core.
3) How can you demonstrate the effect of first touch on your OpenMP implementation with minimal code changes? Illustrate the performance for both cases, i.e. when benefiting from the effect of first touch and when not benefiting from it.
4) Do loop scheduling strategies affect first touch? If yes, why? If not, why not?
5) Enter the wall clock time for both cases of 3) for 12 threads and n=40,000 on LCC3 in the comparison spreadsheet.

## Exercise 2 (1.5 Points)

### Description

This exercise consists of implementing a program that calculates Delannoy numbers with OpenMP tasks.

A Delannoy number specifies the number of paths from the south-west corner of a 2D grid to the north-east corner, using only the per-step directions north, north-east, and east. See https://en.wikipedia.org/wiki/Delannoy_number for more information and a visualization.

### Tasks

1) Implement a sequential program that computes the Delannoy number for a square 2D grid of size NxN where N is an input parameter for your program. Use the naive approach, hence base your implementation on the formula given in the Wikipedia article under "basic recurrence relation". Make sure your program is semantically correct by comparing the result against the precomputed Delannoy numbers given in the article.
2) Parallelize your program using OpenMP tasks and benchmark both the sequential and parallel implementation for several N between 3 and ~15. What can you observe?
3) What is the main bottleneck of your parallel implementation and how can it be improved without changing the underlying algorithm?
4) Enter the wall clock time of the sequential version and the parallel version for 1 and 12 threads for N=12 on LCC3 in the comparison spreadsheet.

## General Notes

All the material required by the tasks above (e.g., code, figures, text, etc...) must be part of the solution that is handed in. Your experiments should be reproducible and comparable to your measurements using the solution materials that you hand in.

**Every** member of your group must be able to explain the given problem, your solution, and possible findings. You may also need to answer detailed questions about any of these aspects.
