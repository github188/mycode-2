.PHONY:
all: test_base64 test_client test_digit test_gnu test_or test_pthread test_pthread_with_lock test_pthread_with_sync test_regex test_sqlite3 test_xml test_const test_list test_logging test_map test_multimap test_string test_unorderedmap test_curl
	@ctags * ../../include/*
clean:
	rm *.o
	rm test_base64 test_client test_digit test_gnu test_or test_pthread test_pthread_with_lock test_pthread_with_sync test_regex test_sqlite3 test_xml test_const test_list test_logging test_map test_multimap test_string test_unorderedmap test_curl


test_base64.o: test_base64.c
test_client.o: test_client.c
test_digit.o: test_digit.c
test_gnu.o: test_gnu.c
test_or.o: test_or.c
test_pthread.o: test_pthread.c
test_pthread_with_lock.o: test_pthread_with_lock.c
test_pthread_with_sync.o: test_pthread_with_sync.c
test_regex.o: test_regex.c
test_sqlite3.o: test_sqlite3.c
test_xml.o: test_xml.c
test_const.o: test_const.cc
test_list.o: test_list.cc
test_logging.o: test_logging.cc ../../include/logging.h
test_map.o: test_map.cc
test_multimap.o: test_multimap.cc
test_string.o: test_string.cc
test_unorderedmap.o: test_unorderedmap.cc
test_curl.o: test_curl.c
../../include/logging.o: ../../include/logging.cc ../../include/logging.h


test_logging: test_logging.o ../../include/logging.o
	$(CXX) -o $@ $^

test_string: test_string.o
	$(CXX) -o $@ $^

test_map: test_map.o
	$(CXX) -o $@ $^

test_unorderedmap: test_unorderedmap.o
	$(CXX) -o $@ $^

test_multimap: test_multimap.o
	$(CXX) -o $@ $^

test_base64: test_base64.o
	$(CXX) -o $@ $^ -lssl

test_const: test_const.o
	$(CXX) -o $@ $^

test_regex: test_regex.o
	$(CXX) -o $@ $^

test_sqlite3: test_sqlite3.o
	$(CXX) -o $@ $^ -lsqlite3

test_list: test_list.o
	$(CXX) -o $@ $^

test_pthread: test_pthread.o
	$(CXX) -pthread -o $@ $^

test_pthread_with_sync: test_pthread_with_sync.o
	$(CXX) -pthread -o $@ $^

test_pthread_with_lock: test_pthread_with_lock.o
	$(CXX) -pthread -o $@ $^

test_curl: test_curl.o
	$(CC) -lcurl -o $@ $^

install: test_regex test_logging test_sqlite3 test_list
	cp $^ ../../bin

test_list.o: test_list.cc

CPPFLAGS=-I ../../include/
CFLAGS=-g -O0
CXXFLAGS=-g -O0 -Wall -Wextra -std=c++0x
