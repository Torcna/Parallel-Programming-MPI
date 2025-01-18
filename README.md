[![Build application](https://github.com/learning-process/ppc-2024-autumn/actions/workflows/main.yml/badge.svg)](https://github.com/learning-process/ppc-2024-autumn/actions/workflows/main.yml)
[![codecov](https://codecov.io/gh/learning-process/ppc-2024-autumn/graph/badge.svg?token=qCOtqeFyIz)](https://codecov.io/gh/learning-process/ppc-2024-autumn)

# Parallel-Programming-MPI
> All my work is located in the branch [baranov_a_branch](https://github.com/learning-process/ppc-2024-autumn/tree/baranov_a_branch)

## Implemented tasks:
- **Number of Orderly Violations**  
- **Ring Topology**  
- **Odd-Even Merge Sort**

## 0. Download all submodules
  ```
  git submodule update --init --recursive --depth=1
  ```
## 1. Set up your environment
### Static analysis of project (optional)
  * **Windows (MSVC)**:
  
  Unsupported operating system!
  
  * **Ubuntu / Debian (`gcc` and `clang`)**:
  ```
  sudo apt install -y cppcheck
  ```

  * **NixOS / Nix (with flakes enabled)**:
  ```
  nix develop .
  ```

  * **MacOS (apple clang)**:
  ```
  brew install cppcheck
  ```

### Code style analysis
Please, follow [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html).

Code style is checked using [clang-format](https://clang.llvm.org/docs/ClangFormat.html) tool.

### Parallel programming technologies
### `MPI`
  * **Windows (MSVC)**:
  
  [Installers link.](https://www.microsoft.com/en-us/download/details.aspx?id=105289) You have to install `msmpisdk.msi` and `msmpisetup.exe`.
  
  * **Ubuntu / Debian (`gcc` and `clang`)**:
  ```
  sudo apt install -y mpich openmpi-bin libopenmpi-dev
  ```
  
  * **NixOS / Nix (with flakes enabled)**:
  ```
  nix develop .
  ```

  * **MacOS (apple clang)**:
  ```
  brew install open-mpi
  ```

### `OpenMP`
  
  `OpenMP` is included into `gcc` and `msvc`, but some components should be installed additionally:
  
  * **Ubuntu / Debian (`gcc` and `clang`)**:
  ```
  sudo apt install -y libomp-dev
  ```

  * **NixOS / Nix (with flakes enabled)**:
  ```
  nix develop .
  ```

  * **MacOS (`llvm`)**:
  ```
  brew install llvm
  brew install libomp
  ```

### `TBB`
  * **Windows (`MSVC`)**, **Linux (`gcc` and `clang`)**, **MacOS (apple clang)**: 
    * Build as 3rdparty in the current project

### `std::thread`
  * `std::thread` is included into STL libraries.

## 2. Build the project with `CMake`
Navigate to a source code folder.

1. Configure the build: `Makefile`, `.sln`, etc.

  ```
  mkdir build && cd build
  cmake -D USE_SEQ=ON -D USE_MPI=ON -D USE_OMP=ON -D USE_TBB=ON -D USE_STL=ON -D USE_FUNC_TESTS=ON -D USE_PERF_TESTS=ON -D CMAKE_BUILD_TYPE=Release ..
  ```
*Help on CMake keys:*
- `-D USE_SEQ=ON` enable `Sequential` labs (based on OpenMP's CMakeLists.txt).
- `-D USE_MPI=ON` enable `MPI` labs.
- `-D USE_OMP=ON` enable `OpenMP` labs.
- `-D USE_TBB=ON` enable `TBB` labs.
- `-D USE_STL=ON` enable `std::thread` labs.
- `-D USE_FUNC_TESTS=ON` enable functional tests.
- `-D USE_PERF_TESTS=ON` enable performance tests.
- `-D USE_CPPCHECK=ON` enable cppcheck.
- `-D CMAKE_BUILD_TYPE=Release` required parameter for stable work of repo.

*A corresponding flag can be omitted if it's not needed.*

2. Build the project:
  ```
  cmake --build . --config RELEASE
  ```
3. Check the task
  * Run `<project's folder>/build/bin`
