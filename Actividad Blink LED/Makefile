PRG = main
SOURCE = main.c
PROGRAMMER = usbasp

MCU = atmega328p

CC = avr-gcc



OBJCOPY = avr-objcopy
OBJDUMP = avr-objdump

clean:
	rm -rf *.o $(PRG)
	rm -rf *.hex

ofile:
	$(CC) $(SOURCE) -o $(PRG) -Wall -Os -mmcu=$(MCU)

text: hex

hex: $(PRG).hex

%.hex:
	$(OBJCOPY) -O ihex $(PRG) $(PRG).hex

all: ofile hex

install: clean all
	sudo avrdude -p $(MCU) -c $(PROGRAMMER) -v -U flash:w:$(PRG).hex:i //-F