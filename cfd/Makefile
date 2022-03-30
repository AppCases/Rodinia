
CC := nvcc

GPU_ARCH ?=

NVCC_FLAG := -g -lineinfo $(GPU_ARCH)

COMMON_INC=./common/inc

COMMON_LIB=./common/lib


all: euler3d euler3d_double  pre_euler3d  pre_euler3d_double 

euler3d: euler3d.cu
	$(CC) $(KERNEL_DIM) -O2 -Xptxas -v $(NVCC_FLAG) euler3d.cu -o euler3d -I$(COMMON_INC)  -L$(COMMON_LIB)

euler3d_double: euler3d_double.cu
	$(CC) -Xptxas -v -O3 $(NVCC_FLAG) euler3d_double.cu -o euler3d_double -I$(COMMON_INC)  -L$(COMMON_LIB)


pre_euler3d: pre_euler3d.cu
	$(CC) -Xptxas -v -O3 $(NVCC_FLAG) pre_euler3d.cu -o pre_euler3d -I$(COMMON_INC)  -L$(COMMON_LIB)

pre_euler3d_double: pre_euler3d_double.cu
	$(CC) -Xptxas -v -O3 $(NVCC_FLAG) pre_euler3d_double.cu -o pre_euler3d_double -I$(COMMON_INC)  -L$(COMMON_LIB)

clean:
	rm -f euler3d euler3d_double pre_euler3d pre_euler3d_double *.linkinfo density* momentum
