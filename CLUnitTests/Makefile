NAME=CLUnitTests
# Exclude the generated file from the wildcard, then add it explicitly below
# so it is always compiled even on a fresh build (it does not exist when the
# Makefile is parsed).
CPPSRC:=$(filter-out cltest.cpp,$(wildcard *.cpp))

all:
	cat ../clMath/secp256k1.cl secp256k1test.cl > cltest.cl
	${BINDIR}/embedcl cltest.cl cltest.cpp _secp256k1_test_cl

	${CXX} -o clunittest.bin ${CPPSRC} cltest.cpp ${INCLUDE} -I${OPENCL_INCLUDE} ${CXXFLAGS} ${LIBS} -L${OPENCL_LIB} -lclutil -lutil -lOpenCL
	mkdir -p $(BINDIR)

	cp clunittest.bin $(BINDIR)/clunittest



clean:
	rm -rf *.a *.o clunittest.bin cltest.cl cltest.cpp
