-- -
In this page we'll discuss how to write to a pin then on how to write to an pin in c. These are the basics of understanding of how to use 8-bit AVR. I'll be using an arduino mega(Atmega 2560).

+ [[#configuring as output]]
+ [[#configuring as input]]

# quickly explained section
-- -
So on bare-metal AVR without the the Arduino library we'll need to be setting the pin-outs on the board it self. First of all, well need to set the **DDR** -> data direction register. Each port has one.

What is an port? You may ask.

Well its this finicky thing on the chip its self. Each I/O _pin_ belongs to **port**. These are like arrays, you can sorta think. It ill become much clearer later on. Later is now, haha.

So quickly, each pin belongs to an port and there usually as far is i know multiple ports on an Atmel IC. Each port stores values corresponding to each pin. And as you can maybe guess the value on each data segment of that *port array*. Will depict if the pin is an **output** or an **input**. A 1 means _output_ and a 0 is an _input_.

**_Note!_**: You can find the **DDR**x or _data direction register_ data in the "_Ports as General Digital I/O_" section on the official Atmega [datasheet](https://ww1.microchip.com/downloads/en/devicedoc/atmel-2549-8-bit-avr-microcontroller-atmega640-1280-1281-2560-2561_datasheet.pdf).

Before you we move on you should read [[packages, make file, avr lib and .clangd file]]. To setup your enviroment.
## configuring as output
-- -
I'll show you the code first, then explain.
```c
#include <avr/io.h>

int main(void)
{
	DDRB |= (1 << PB2); // pin 24 on arduino named PB2
}
```

So in layman's terms we set `DDRB` or _data direction register b_ equal to `DDRB` or 1 shifted by the pin. This will set pin `PB2` or `pin24` on the Arduino Mega to a 1 witch is the **write** value. On the _data direction register_.
### writing
This code will set `PB2` or `pin24` to **HIGH** -> 1.
```c
#include <avr/io.h>

int main(void)
{
	DDRB |= (1 << PB2); // pin 24 on arduino named PB2
	// --
	PORTB |= (1 << PB2); // write high on the the an register of the port A array
}
```

**_Note!:_** They might no be actual arrays in reality but think of them like this.

So this code will of course shift `1` by `PB2` on the `PORTA` or `PORTA`, witch will make it HIGH. You may ask, why are they named **PORTA** and **PB2**? well its to make the code portable across different **MCU**'s. The compiler will do the rest.

And now how to set a bit to 0.
```c
#include <avr/io.h>

int main(void)
{
	DDRB |= (1 << PB2); // pin 24 on arduino named PB2
	// --
	PORTA |= ~(1 << PB2); // write low on the the an register of the port A array
}
```

So this will translate to, The inverse of 1 shifted by `PB2` on PORTA or PORTA. so...
```c 
#include <avr/io.h>

int main(void)
{
	DDRB |= (1 << PB2); // pin 24 on arduino named PB2
	// --
	PORTA |= ~(1 << PB2); // write low on the the an register of the port A array
	PORTA = PORTA | ~(1 << PB3); // the same as the line above
}
```

Will do the same thing. On `PB2` and `PB3`.
## configuring as input
-- -
The following code will configure `pin26` or better said `PA4` on the Arduino mega as in input.
```c
#include <avr/io.h>

int main(void) {
	DDRA &= ~(1 << PA4);
}
```

The Atmega 2560 has build in pull resistors, but using these will change how you read from the pin. So in the follewing example will set the internal pull-resistor to **off**.

```c
#include <avr/io.h>

int main(void) {
	DDRA &= ~(1 << PA4); // turn on read mode on PA
	PORTA &= ~(1 << PA4); // turn of pull up resistor
}
```

And vice versa the **on** code.

```c
#include <avr/io.h>

int main(void) {
	DDRA &= ~(1 << PA4); // turn on read mode on PA
	PORTA &= (1 << PA4); // turn on pull resistor
}
```
### reading
The following `if` statement will read from pin 26 on the Arduino mega.

```c
if (PINA & (1 << PA4)) { // read from PA4
	// do something in here
}
```

**_Note!:_** You can set a alias for a pin using `#define`.