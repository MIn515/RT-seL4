CC=riscv64-unknown-linux-gnu-g++

all:
	$(CC) -static -o runner \
		-I$(KEYSTONE_SDK_DIR)/include/host/ \
		-I$(KEYSTONE_SDK_DIR)/include/edge/ \
		host.cpp \
		$(KEYSTONE_SDK_DIR)/lib/libkeystone-host.a \
		$(KEYSTONE_SDK_DIR)/lib/libkeystone-edge.a
