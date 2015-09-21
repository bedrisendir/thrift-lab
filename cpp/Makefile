GEN_SRC := src/* gen-cpp/*
GEN_OBJ := $(patsubst %.cpp,%.o, $(GEN_SRC))

.SILENT:
THRIFT_PATH=/home/yaoliu/src_code/local/include
LIB_PATH=/home/yaoliu/src_code/local/lib

.PHONY: all clean

all:	clean server client

bin/%.o: src/%.cpp
	echo "test"
	g++ -Wall -DHAVE_INTTYPES_H -DHAVE_NETINET_IN_H -I$(THRIFT_PATH) -Isrc/ -c $< -o $@

server:	bin/CppServer.o $(GEN_OBJ)
	g++ $^ -o $@ -L$(LIB_PATH) -lthrift 

client: bin/CppClient.o $(GEN_OBJ)
	g++ $^ -o $@ -L$(LIB_PATH) -lthrift 

clean:
	rm -rf bin/

