#!/bin/sh
#
# Makefile for OSHUN
# This should work with gcc-6, open-mpi compiled with gcc-6, and HDF5 compiled with c++11 standards

COMPILER = g++-7

# GNU compilers#
OPTFLAGS1 = -O3
OPTFLAGSt = -O2 -no-vec
OPTFLAGS2 = -O1
DBGFLAGS = -v -O0 -Wall -Wuninitialized -Wextra -Wpedantic
# -O3 -ffast-math -ftree-loop-distribution -fno-signed-zeros -ftree-loop-ivcanon -ftree-vect-loop-version
#-fopt-info-vec-optimized  
# INTEL compilers
#OPTFLAGS1 = -O3
#OPTFLAGS1 = -g -O0 -Wall

# HDF5 libraries
H5LIB = -lhdf5_hl -lhdf5
MPILIB = -lmpi
LDFLAGS = -L/usr/local/Cellar/hdf5/1.10.1_2/lib -L/usr/local/Cellar/gcc/7.2.0/lib/gcc/7
CPPFLAGS = -fopenmp
INCLUDE_DIRS = -L/usr/local/Cellar/hdf5/1.10.1_2/include -I/usr/local/opt/gcc/lib/gcc/7

EXEC_DIR = ../bin
TMP_DIR = ../bin/tmp

OBJECTS = input.o clock.o state.o formulary.o parser.o setup.o vlasov.o nmethods.o functors.o collisions.o fluid.o particletracker.o implicitE.o parallel.o export.o main.o

EXEC = oshun.e

BUILDOBJECTS = ${addprefix ${TMP_DIR}/,${OBJECTS}}

BUILDEXEC = ${addprefix ${EXEC_DIR}/,${EXEC}}

${BUILDEXEC} : ${BUILDOBJECTS}
	-${COMPILER} ${CPPFLAGS} ${OPTFLAGS2} ${INCLUDE_DIRS} ${LDFLAGS} $(H5LIB) $(MPILIB) -o ${BUILDEXEC}  \
	${BUILDOBJECTS} 

clean ::
	rm -f ${BUILDOBJECTS}
	rm -f ${BUILDEXEC}
	rm -f ${TMP_DIR}/${BUILDOBJECTS}

debug :
	${COMPILER} ${OPTFLAGS1} -o ${BUILDEXEC} \
	%.cpp

${TMP_DIR}/parser.o: parser.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<		

${TMP_DIR}/input.o: input.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/clock.o: clock.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/state.o: state.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<	

${TMP_DIR}/formulary.o: formulary.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<	

${TMP_DIR}/setup.o: setup.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<	

${TMP_DIR}/vlasov.o: vlasov.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<	

${TMP_DIR}/nmethods.o: nmethods.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS2) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/functors.o: functors.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/collisions.o: collisions.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/fluid.o: fluid.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/particletracker.o: particletracker.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/implicitE.o: implicitE.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/parallel.o: parallel.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/export.o: export.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<

${TMP_DIR}/main.o: main.cpp
	$(COMPILER) ${CPPFLAGS} $(OPTFLAGS1) $(INCLUDE_DIRS) -c -o $@ $<		
	#