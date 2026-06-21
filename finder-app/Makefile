# finder-app/Makefile
# Default target: build writer for the native platform.
# Cross-compile (manual):   make CROSS_COMPILE=aarch64-none-linux-gnu-
# Cross-compile (Buildroot): CC provided externally; we honor it.

CROSS_COMPILE ?=

# Only define CC when the user (env or command line) has not.
# Make builtin defaults have origin "default" and should be replaced with
# our $(CROSS_COMPILE)gcc default.
ifeq ($(origin CC),default)
CC := $(CROSS_COMPILE)gcc
endif

CFLAGS  = -Wall -Wextra -g
TARGET  = writer
OBJS    = writer.o

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) -o $(TARGET) $(OBJS)

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(TARGET) *.o

.PHONY: clean
