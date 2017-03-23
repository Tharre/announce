#
# Makefile for tinysvcmdns
#

CFLAGS += -Wall -pedantic -std=gnu99 -static -fPIE
#CFLAGS += -g
CFLAGS += -O2 -DNDEBUG
LDFLAGS += -pie

ifneq ($(CROSS_COMPILE),)
  CC = gcc
  CC := $(CROSS_COMPILE)$(CC)
  AR := $(CROSS_COMPILE)$(AR)
endif

BIN=announce

LIBTINYSVCMDNS_OBJS = tinysvcmdns.o

.PHONY: all clean

all: $(BIN) libtinysvcmdns.a

clean:
	-$(RM) *.o
	-$(RM) *.bin
	-$(RM) $(BIN)
	-$(RM) libtinysvcmdns.a

tinysvcmdns: tinysvcmdns.o

announce: announce.o libtinysvcmdns.a ifaddrs.o

libtinysvcmdns.a: $(patsubst %, libtinysvcmdns.a(%), $(LIBTINYSVCMDNS_OBJS))

