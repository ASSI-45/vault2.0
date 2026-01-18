-- -
+ In arrays _missing_ elements are **defaulted** to `0`.

```c
int i = 10; // defintion, identifier, declration
int main() {} // defintion, declration
```

+ **Statements** are instructions that tell the compiler what to do.


## chapter 3
-- -
+ `case` values must be integer constants.
+ **Domain iteration** should be coded with a _for_ loop.

## chapter 4
-- -
+ `size_t` represents values in the range [0, SIZE_MAX].
	**_Note!:_** If the number of `size_t` is larger than `SIZE_MAX` then where speakng of an **_arithmetic overflow_**.
+ in case of **_overflow_**, unsigned arithmetic will wrap around. -> `unsigned int i = -1; // SIZE_MAX`
+ The results of `/` and `%` is always smaller or equal to there _operands_. So these _operators_ will **never overflow**.
+ Never modify **more** than one object in you'r statement.

This code is valid.
```c
size_t c = (a < b) + (c < d);
```

+ all logic operators return _false_ or _true_.
+ logic operators in c **can** _short-circuit_.
+ don't use the `,` operator.
+ don't rely on sequencing it will bite you.

## chapter 5 - boring as hell
-- -
+ c uses a **_abstract state machine_**.
+ type determines optimization opportunities.
+ don't use **binary, octal** or **hexadecimal** literals for negative values. use **decimal** literals for the negative ones.
+ use _unsigned_ types where ever you can.

```c 
double C[] = [0] = 6, [3] = 1, ; // is valid code
// these are designated initializers
```

 + `{ }` is a valid initializer for all types.
 + **_ICE_** -> integer constant expressions
 + `<iso646.h>`
 + import `<stdbool.h>` for backwards compatibility.

## chapter 6 - pointers (finally)
-- -
+ **CLA**'s -> constant-length arrays
+ **VLA**'s -> variable-length arrays
+ VLA's can have default initializers
+ VLA's can't be declared outside functions.
+ **_Pointers_** are opaque objects.
+ invalid pointers lead to program failure.
+ `nullptr` will make the pointer `null`.
+ always initialize pointers.
- [ ] what is an `enum`
- 