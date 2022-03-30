CUDA_DIR = /usr/local/cuda

# CUDA toolkit libraries
CUDA_LIB_DIR := $(CUDA_DIR)/lib
ifeq ($(shell uname -m), x86_64)
     ifeq ($(shell if test -d $(CUDA_DIR)/lib64; then echo T; else echo F; fi), T)
     	CUDA_LIB_DIR := $(CUDA_DIR)/lib64
     endif
endif


# C compiler
CC = gcc
CC_FLAGS = -g -fopenmp -O2 

# CUDA compiler
NVCC = $(CUDA_DIR)/bin/nvcc
NVCC_FLAGS = -I$(CUDA_DIR)/include 

# 'make dbg=1' enables NVCC debugging
ifeq ($(dbg),1)
	NVCC_FLAGS += -g -O0
else
#	NVCC_FLAGS += -O2
	NVCC_FLAGS += -O2 -g -lineinfo
endif

# 'make emu=1' compiles the CUDA kernels for emulation
ifeq ($(emu),1)
	NVCC_FLAGS += -deviceemu
endif


kmeans: cluster.o getopt.o kmeans.o kmeans_clustering.o kmeans_cuda.o rmse.o
	$(CC) $(CC_FLAGS) cluster.o getopt.o kmeans.o kmeans_clustering.o kmeans_cuda.o rmse.o -o kmeans -L$(CUDA_LIB_DIR) -lcuda -lcudart -lm

%.o: %.[c]
	$(CC) $(CC_FLAGS) $< -c

kmeans_cuda.o: kmeans_cuda.cu 
	$(NVCC) $(NVCC_FLAGS) -c kmeans_cuda.cu

clean:
	rm -f *.o *~ kmeans kmeans_cuda.linkinfo
