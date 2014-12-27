# Install cxxnet on CentOS via blas

### Prerequisites
- OpenCV
- CUDA Toolkit
- Blas, CBlas, Lapack, Atlas
    - easy to install via yum

### Installation
- `git clone https://github.com/antinucleon/cxxnet.git`
- `cd cxxnet`
- `git clone https://github.com/tqchen/mshadow`
- `make blas=1`

### Possible modification on Makefile
- `CFLAGS += -I/usr/local/cuda/include/`
- `LDFLAGS += -L/usr/local/cuda/lib64`
- `LDFLAGS += -lcblas -latlas -llapack`

### Probable problems
- `/usr/bin/ld: cannot find lcblas`
    - If installed atlas correctly, then use command *locate* to find the corresponding library file.
	- Then link the library file to the desired directory.
	- Specifically:
		- `locate libcblas.so*`
		- `sudo ln -s */libcblas.so /usr/lib/libclas.so`
- When use the tools `im2bin`, you also need to modify the **Makefile** if necessary.
