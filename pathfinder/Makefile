CUDA_DIR = /usr/local/cuda

# CUDA toolkit libraries
CUDA_LIB_DIR := $(CUDA_DIR)/lib
ifeq ($(shell uname -m), x86_64)
     ifeq ($(shell if test -d $(CUDA_DIR)/lib64; then echo T; else echo F; fi), T)
     	CUDA_LIB_DIR := $(CUDA_DIR)/lib64
     endif
endif

CC := $(CUDA_DIR)/bin/nvcc
INCLUDE := $(CUDA_DIR)/include

NVCC_FLAGS ?= -g -lineinfo

SRC = pathfinder.cu

EXE = pathfinder

release:
	$(CC) $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) $(NVCC_FLAGS)

enum:
	$(CC) -deviceemu $(SRC) -o $(EXE) -I$(INCLUDE) -L$$(CUDA_LIB_DIR) $(NVCC_FLAGS)

debug:
	$(CC) -g $(SRC) -o $(EXE) -I$(INCLUDE) -L$$(CUDA_LIB_DIR) $(NVCC_FLAGS)

debugenum:
	$(CC) -g -deviceemu $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) $(NVCC_FLAGS)

clean:
	rm -f pathfinder result.txt