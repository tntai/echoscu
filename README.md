# StoreSCU
File copied from https://github.com/DCMTK/dcmtk/blob/master/dcmnet/apps/echoscu.cc

## Installation steps
1. MS Build
- Download and install Visual Studio build tool

2. Conan
- Install Python
- Install conan 
    ```
    $ pip install conan
    ```

## Compiling steps

1. Create a build directory:

    ```
    $ mkdir build && cd build
    ```

2. Install dependencies:

    ```
    $ conan install ..
    ```
- Add `--build=missing` in case of binary not found 

3. Configure the CMake project (lib is in 64 bits):

    ```
    $ cmake .. -G "Visual Studio 15 2017" -A x64
    ```

4. Build it:

    ```
    $ cmake --build . --config Release
    ```

## Others 
- To see options from package (e.g disable openssl support)
`conan get dcmtk/3.6.6@`