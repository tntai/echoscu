# StoreSCU
File copied from https://github.com/DCMTK/dcmtk/blob/master/dcmnet/apps/echoscu.cc

## Installation steps
1. MS Build
- Download and install Visual Studio build tool

2. Cmake

## Compiling steps

1. Create a build directory:

    ```
    $ mkdir build && cd build
    ```

2. Configure the CMake project (lib is in 64 bits):

    ```
    $ cmake .. -G "Visual Studio 15 2017" -A x64
    ```

3. Build it:

    ```
    $ cmake --build . --config Release
    ```

## Others 
- To see options from package (e.g disable openssl support)
`conan get dcmtk/3.6.6@`