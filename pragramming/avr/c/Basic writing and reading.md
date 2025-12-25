-- -
In this page we'll discuss how to write to a pin then on how to write to an pin in c. These are the basics of understanding of how to use 8-bit AVR. I'll be using an arduino mega(atmel 2560).

# quickly explained section
-- -
So on bare-metal AVR without the the arduino library we'll need to be setting so pin-outs on the board it self. First of all, well need to set the DDA -> data direction register. Each port has one.

What is an port? You may ask.

Well its this finicky thing on the chip its self. Each I/O _pin_ belongs to **port**. These are like arrays, you can sorta think. It ill become much clearer later on. Later is now, haha.

So quickly, each pin belongs to an port and there usually as far is i know multiple ports on an Atmel IC. Each port stores values corresponding to each pin. And as you can maybe guess the value on each data segment of that *port array*.