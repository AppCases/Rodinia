all: avimod.o avilib.o

# compile supporting function file into object (binary)
avimod.o: avilib.h avimod.c 
	gcc -c avimod.c -g

# compile supporting function file into object (binary)
avilib.o: avilib.h avilib.c
	gcc -c avilib.c -g

# delete files
clean:
	rm *.o *.out
