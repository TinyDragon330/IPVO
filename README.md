# IPVO
This is an assigment I got in class. I need to benchmark reads and writes based on hit rate. I use Redis, MySQL and Docker
## Prerequisites
Docker
Git
Python3
## Setup
Setup is simple just clone the repository with command:
```
git clone https://github.com/TinyDragon330/IPVO
```
Or download as zip and unpack.
## Running the benchmark
Everything is automated using jupyter notebooks. Setting up Redis and MySQL and running benchmarks is done by executing blocks of commands in the jupyter notebook.
The purpose of every block of commands is explained in the jupyter notebook
## Benchmark explanation
In this project I'm benchmarking reads and writes from database based on hit rate in cache.
Database used for the project is a MySQL db and Redis is used for cache.
All benchmarks are run on a small dataset of 100 key-value pairs.
### Benchmarks included:
   1. Writing data without cache
   2. Writing data with cache
   3. Reading data without cache
   4. Reading data with 0% cache hit rate
   5. Reading data with 50% cache hit rate
   6. Reading data with 80% cache hit rate
   7. Reading data with 100% cache hit rate
50% cache hit rate means half of the data we are reading is located in cache
## Benchmark results and report
### Benchmark results after running each benchmark 100 times and calculating average execution time:
   1. Writing data without cache: 0.17429688692092896s
   2. Writing data with cache: 0.40509087562561036s
   3. Reading data without cache: 0.19646842479705812s
   4. Reading data with 0% cache hit rate: 0.2993379759788513s
   5. Reading data with 50% cache hit rate: 0.1972200345993042s
   6. Reading data with 80% cache hit rate: 0.18536559581756593s
   7. Reading data with 100% cache hit rate: 0.17112080812454222s
### Explaining the results:
* Writing data with cache implemented is much slower because we are storing data in 2 places
* Benchmark 3 is the base benchmark for reads that we are trying to improve by implementing a cache.
* Benchmark 4 is expectedly slower because we never find the data we are looking for in cache and have to look for it in database so it's benchmark 3 time + time it takes to check cache
* Benchmark 5 is in this result about very similar to benchmark 3 but still slower
* Benchmark 6 is faster than benchmark 3 in this result and we see cache improve read times
* Benchmark 7 is the fastes with further improvements to read times
### Problems with these results and benchmarks
These benchmarks are very inconsistent. Even if the benchmark executes reads 100 times, the results largely variate to the point that benchmark 7 can get slower results than benchmark 3.
There are a few reasons as to why this may be the case:
* I'm inexperienced and my implementation of the cache and database is bad
* I'm inexperienced and my benchmark is bad
* Every benchmark generates a new dataset and and results may be different because of that (possible solution is using one dataset for all benchmarks).
* Datasets generated are bad. The data I generate has only 2 columns (key and value)
* The inconsistency is not a mistake and I don't know how to explain it correctly
