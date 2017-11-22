# Immix

This is a staging area for pluggable implementation of Immix garbage collector.

## Building Immix
1. Make sure you have [CMake](https://cmake.org/) 3.6 or newer installed:
  ```sh
  $ cmake -version
  ```

2. Clone the [source](https://github.com/scala-native/immix) with git:
  ```sh
  $ git clone https://github.com/scala-native/immix.git
  $ cd immix
  ```

3. Build:
  ```sh
  $ cmake . && make
  ```
