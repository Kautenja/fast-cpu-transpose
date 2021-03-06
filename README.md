# Fast CPU Transpose 

[![Build Status][build-status]][build-server]

[build-status]: https://travis-ci.org/Kautenja/fast-cpu-transpose.svg?branch=master
[build-server]: https://travis-ci.org/Kautenja/fast-cpu-transpose

Completed for Lab 3 of COMP7300, Advanced Computer Architecture, at Auburn University.

## Usage

### Compilation

The code uses threads with `-pthread` flag. The usage of the `-Ofast` flag
enables all compile-time optimizations.

```shell
cc -Ofast -pthread <code_file> -o <output_executable>
```

##### Example

```shell
cc -Ofast -pthread rowwise.c -o rowwise
```

### Test Automation

The 5 test runs are automated with a shell script. Make sure the permissions
are set correctly first by executing the following from the top level of the
project:

```shell
chmod 0755 ./run.sh
```

A test can be executed using the following command from the top level:

```shell
./run.sh <code file name>
```

This will route the shell output to a file in the [`build`](./build) directory
called `<code file name>.out`. Note that the `.c` **IS NOT** included in this
command.

##### Example

To run the default provided code (adjusted for 7 tests):

```shell
./run.sh myInitializeMatrix
```

#### [`rowwise.c`](./rowwise.c)

contains the code for row-wise initialization and transpose. To compile and run
the row-wise initialization (and optimized transposition):

```shell
mkdir -p build
cc -Ofast -pthread rowwise.c -o build/rowwise
./build/rowwise
```

To compile and run the 5 consecutive tests saving the output to a file:

```shell
./run.sh rowwise
```

#### [`columnwise.c`](columnwise.c)

contains the code for column-wsie intialization and transpose. To compile and
run the column-wise initialization (and optimized transposition):

```shell
mkdir -p build
cc -Ofast -pthread columnwise.c -o build/columnwise
./build/columnwise
```

To compile and run the 5 consecutive tests saving the output to a file:

```shell
./run.sh columnwise
```

