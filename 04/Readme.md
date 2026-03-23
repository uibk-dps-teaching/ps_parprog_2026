# Assignment 4

## Exercise 1 (1.5 Points)

### Description

Last week you were tasked with implementing a program that calculates the [Mandelbrot set](https://en.wikipedia.org/wiki/Mandelbrot_set), and then think about possible parallelizations.
```text
function calc_mandelbrot(image):
    for each (X,Y) do:
        x = 0.0
        y = 0.0
        cx = mapped x_pixel_idx to Mandelbrot x-axis [-2.5, 1]
        cy = mapped y_pixel_idx to Mandelbrot y-axis [-1, 1]
        iteration = 0
        while (x*x + y*y <= 2*2 AND iteration < MAX_ITER) do:
            x_tmp = x*x - y*y + cx
            y = 2*x*y + cy
            x = x_tmp
            iteration = iteration + 1

        norm_iteration = mapped iteration to pixel range [0, 255]
        image[y_pixel][x_pixel] = norm_iteration
```

### Tasks

1) Implement a parallelized version of the mandelbrot calculation using `Posix Threads`
2) Benchmark your implementation using 1, 2, 4, 8 and 12 threads
3) Visualize your measurements and enter the times for 1 and 12 threads into the performance comparison spreadsheet.

>You can reuse last weeks code as much as you want, the focus of this exercise is making you more comfortable with parallel programming ideas and pitfalls.

>If you do not have your own serial implementation, just send your instructor a message and he will provide you with one.

---
## Exercise 2 (1.5 Points)

### Description

The Hadamard product is defined as the element-wise product of two matrices with the same dimensions. The following two snippets give an implementation of the Hadamard product for n x n square matrices.

```C
for (size_t j = 0; j < n; ++j) {
    for (size_t i = 0; i < n; ++i) {
        c[i][j] = a[i][j] * b[i][j];
    }
}
```

```C
for (size_t i = 0; i < n; ++i) {
    for (size_t j = 0; j < n; ++j) {
        c[i][j] = a[i][j] * b[i][j];
    }
}
```

### Tasks

1) For both implementations, give a function f to calculate the number of data cache read misses for the matrix size n and the cache line size s in an 8-way set-associative cache. Assume that all variables are initialized appropriately (the matrix elements are of type `int32_t`) and that the matrices are stored in contiguous memory in row-major order. Additionally, the matrices are too large to store them entirely in the cache (n >> s).
2) Use the two snippets to implement two versions of the Hadamard product.
3) Log into the LCC3 cluster and analyze the cache behavior of the implementations using `cachegrind` (e.g. `valgrind --tool=cachegrind <your program>`) and `perf` (e.g. `perf stat -e LLC-load-misses -e LLC-store-misses <your program>`) Can you validate your theoretical findings? Compare the results of both tools.
