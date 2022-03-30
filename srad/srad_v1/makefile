CUDA_DIR = /usr/local/cuda

# CUDA toolkit libraries
CUDA_LIB_DIR := $(CUDA_DIR)/lib
ifeq ($(shell uname -m), x86_64)
     ifeq ($(shell if test -d $(CUDA_DIR)/lib64; then echo T; else echo F; fi), T)
     	CUDA_LIB_DIR := $(CUDA_DIR)/lib64
     endif
endif


CC := $(CUDA_DIR)/bin/nvcc

CUDA_ARCH := -arch sm_86

NVCC_FLAFS := -c -O3 $(CUDA_ARCH) -g -lineinfo

INCLUDE := $(CUDA_DIR)/include

# Example
# target: dependencies
	# command 1
	# command 2
          # .
          # .
          # .
	# command n

# link objects(binaries) together
a.out:		main.o
	$(CC)	main.o \
				-I$(INCLUDE) \
				-L$(CUDA_LIB_DIR)  \
				-lm -lcuda -lcudart -o srad $(NVCC_FLAFS)

# compile main function file into object (binary)
main.o: 	main.cu \
				define.c \
				graphics.c \
				extract_kernel.cu \
				prepare_kernel.cu \
				reduce_kernel.cu \
				srad_kernel.cu \
				srad2_kernel.cu \
				compress_kernel.cu
	nvcc	main.cu \
				$(NVCC_FLAFS)

# delete all object files
clean:
	rm  -f *.o srad
