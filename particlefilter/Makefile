#makefile

CUDA_DIR = /usr/local/cuda

# CUDA toolkit libraries
CUDA_LIB_DIR := $(CUDA_DIR)/lib
ifeq ($(shell uname -m), x86_64)
     ifeq ($(shell if test -d $(CUDA_DIR)/lib64; then echo T; else echo F; fi), T)
     	CUDA_LIB_DIR := $(CUDA_DIR)/lib64
     endif
endif

CC := $(CUDA_DIR)/bin/nvcc

CUDA_ARCH ?= -arch sm_86

NVCC_FLAGS := -lcuda -g -lm -O3 -use_fast_math $(CUDA_ARCH)

INCLUDE := $(CUDA_DIR)/include

all: naive float

naive: ex_particle_CUDA_naive_seq.cu
	$(CC) -I$(INCLUDE) -L$(CUDA_LIB_DIR) $(NVCC_FLAGS) ex_particle_CUDA_naive_seq.cu -o particlefilter_naive
	
float: ex_particle_CUDA_float_seq.cu
	$(CC) -I$(INCLUDE) -L$(CUDA_LIB_DIR) $(NVCC_FLAGS) ex_particle_CUDA_float_seq.cu -o particlefilter_float

clean:
	rm particlefilter_naive particlefilter_float
