## 01 - SAXPY
Implementation of the *scaled vector addition of single-precision floating point data* operation.

#### Requirements
The Intel TBB library is required.

#### Compile and run
Compile with

```g++ -std=c++11 -Wall -Wextra -O3 main.cpp -ltbb -o main```

or

```icc -std=c++11 -Wall -Wextra -O3 main.cpp -ltbb -o main```

The application can be run as ```./main``` without parameters.

<br>

## 02 - Mandelbrot Set
Implementation of the [Mandelbrot set](https://en.wikipedia.org/wiki/Mandelbrot_set), i.e. the set of all points c in the complex plane for which the quadratic function   
z = z<sup>2</sup> + c does not go to infinity when iterated from z = 0. A plot of the Mandelbrot set can be obtained by coloring values of c in the complex plane according to the number of steps required to reach r<sub>max</sub> = 2.<ul><li><b>Exercise 1:</b> sequential implementation that uses the [SDL2](https://wiki.libsdl.org/) library to draw in a separated window the frames containing the plots produced by iterating the Mandelbrot set computation.
#### Requirements
The SDL2 library is required.
#### Compile and run
A Makefile has been provided. The application can be run as ```./main``` without parameters.
#### Interaction with the application
The user can terminate the process by closing the window or by pressing ```q``` on the keyboard to quit.</li><li><b>Exercise 2:</b> sequential and parallel implementation with ```tbb::parallel_for``` of the Mandelbrot set computation. A plot is generated as [.ppm](http://paulbourke.net/dataformats/ppm/) file.
#### Requirements
The Intel TBB library is required.
#### Compile and run
A Makefile has been provided. The application can be run as

```./main par_deg width height max_iter```

where ```par_deg = 0``` means sequential execution and ```par_deg > 0``` means parallel execution. ```par_deg``` is a mandatory parameter while the others are optional and can be used to set the dimensions of the matrix ```width``` and ```height``` and the maximum number of iterations ```max_iter```.</li><li><b>Exercise 3:</b> parallel implementation of the Mandelbrot set computation that exploits ```tbb::parallel_for``` construct using in one case the default number of threads and in another case only one thread. This is done by setting the appropriate parameters of the [```tbb::task_scheduler_init```](https://www.threadingbuildingblocks.org/docs/doxygen/a00150.html) class.
<!--
Other info here: https://software.intel.com/en-us/node/506296
-->
#### Requirements
The Intel TBB library is required.
#### Compile and run
A Makefile has been provided. The application can be run as

```./main width height max_iter```

where ```width``` and ```height``` are the dimensions of the matrix and ```max_iter``` is the maximum number of iterations for the computation.</li><li><b>Exercise 4:</b> extension of the previous exercise where an array of buckets (implemented as a [```tbb::concurrent_hash_map```](https://www.threadingbuildingblocks.org/docs/help/reference/containers_overview/concurrent_hash_map_cls.html)) has been used to count how many times a certain number of iterations shows up during the whole computation. Requirements, compilation and instructions to run the program are the same of <b>Exercise 3</b>.
<!--
Other info on concurrent hash map:
https://software.intel.com/en-us/node/506077
https://stackoverflow.com/questions/23501591/tbb-concurrent-hash-map-find-insert
https://software.intel.com/en-us/blogs/2010/05/14/traversing-concurrent_hash_map-concurrently
-->
</li></ul>
