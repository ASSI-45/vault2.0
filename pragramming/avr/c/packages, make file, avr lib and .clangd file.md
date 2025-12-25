-- -
The packages for debian.
```bash
sudo apt install -y avr-libc avrdude binutils-avr gcc-avr
```

Here is a common make file chatgpt wrote for me. But first find the tty port thingy.

```bash
ls /dev/ | grep ACM
```

```c
# ===== Project settings =====
PROJECT = main
MCU     = atmega2560
F_CPU   = 16000000UL
BAUD    = 115200
PORT    = /dev/ttyACM0        # Change for your system
PROGRAMMER = wiring

# ===== Toolchain =====
CC      = avr-gcc
OBJCOPY = avr-objcopy
SIZE    = avr-size
AVRDUDE = avrdude

# ===== Flags =====
CFLAGS = -mmcu=$(MCU) \
         -DF_CPU=$(F_CPU) \
         -Os \
         -Wall \
         -std=c11

LDFLAGS = -mmcu=$(MCU)

# ===== Files =====
SRC = $(PROJECT).c
OBJ = $(PROJECT).o
ELF = $(PROJECT).elf
HEX = $(PROJECT).hex

# ===== Targets =====
all: $(HEX)

$(ELF): $(OBJ)
	$(CC) $(LDFLAGS) $^ -o $@
	$(SIZE) $@

$(OBJ): $(SRC)
	$(CC) $(CFLAGS) -c $< -o $@

$(HEX): $(ELF)
	$(OBJCOPY) -O ihex -R .eeprom $< $@

flash: $(HEX)
	$(AVRDUDE) -p $(MCU) -c $(PROGRAMMER) -P $(PORT) -b $(BAUD) -D -U flash:w:$(HEX)

clean:
	rm -f *.o *.elf *.hex

.PHONY: all flash clean

```

**_Warning:_** This make file only works with a single `main.c` fille.
# usage
```bash
make        # compile
make flash  # upload to ATmega2560
make clean  # remove build files
```

# structure
```
project/
├── Makefile
└── main.c
```

# lib and boiler plate
```c
#include <avr/io.h>

#define SAFE_EXIT 0
#define UNSAFE_EXIT 1

int main(void)
{
	
	return SAFE_EXIT;
}
```

# .clangd
This file should me included to get nvim-lsp working
```c
CompileFlags:
  Add:
    - --target=avr
    - -mmcu=atmega328p
    - -I/usr/lib/avr/include
    - -I/usr/avr/include
    - -DF_CPU=16000000UL

```