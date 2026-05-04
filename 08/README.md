# Assignment 8

The goal of this assignment is to work with data dependencies.

## Exercise 1 (1.5 Points)

### Description

- Compilers often perform dependence analysis as a pre-step in order to safely perform optimizations such as vectorization in a second step. In this exercise, we will look at the first step only, namely compiler capabilities and reporting.

### Tasks

1) Compile the given program [analysis.c](analysis.c) with gcc 12.2.0 (`module load  gcc/12.2.0-gcc-8.5.0-p4pe45v`) and the flags `-O2 -ftree-vectorize -fopt-info-vec-all-internals`.
2) Examine the output. What information about dependence analysis can you find in the output? Can you identify any information pointing to successful or unsuccessful vectorization? Does the compiler perform any analysis beyond checking for dependencies and semantic correctness? What are your findings?

## Exercise 2 (1.5 Points)

### Description

Investigate the following given code examples along with their task.

### Tasks

1) Investigate the given code excerpt. Can this code be safely parallelized manually? Can this code be safely parallelized by the compiler?

    ```C
    void copy(double* x, double* y) {
        for(int i = 0; i < 1024; i++) {
            x[i] = y[i];
        }
    }
    ```

2) Normalize the following loop nest:

    ```C
    for (int i=4; i<=N; i+=9) {
        for (int j=0; j<=N; j+=5) {
            A[i] = 0;
        }
    }
    ```

3) Does the following code excerpt hold any dependencies? If not, how would you parallelize it? If yes, what are the distance and direction vectors?

    ```C
    for(int i = 1; i < N; i++) {
        for(int j = 1; j < M; j++) {
            for(int k = 1; k < L; k++) {
                a[i+1][j][k-1] = a[i][j][k] + 5;
            }
        }
    }
    ```

## General Notes

All the material required by the tasks above (e.g., code, figures, text, etc...) must be part of the solution that is handed in. Your experiments should be reproducible and comparable to your measurements using the solution materials that you hand in.

**Every** member of your group must be able to explain the given problem, your solution, and possible findings. You may also need to answer detailed questions about any of these aspects.
