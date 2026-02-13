-- -
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
- [x] what is an `enum`
#### how to write an struct
```c
struct tm today {
	.tm_year = 2026,
	.tm_month = 01,
	.tm_day = 24
}
```

- structures cannot be compared with == or !=
- structure layout is important design decision
- there can be padding after struct member
- no padding of the beginning of a structure
- identifier names terminating with `_t` are reserved
### summary chapter 6
- Arrays combine several types of the same type in to an object
- Pointers either refer to other objects, are null, or are invalid
- Structures combine values of different base types in to one object
- `typedef` provides new names for existing types

## chapter 7 - functions
-- -
 - all functions must have an prototype
 - Functions have only one entry but can have several **return**s statements
 - if an end function call is **void** then the **return** can be omitted, and this is only allowed for **void** functions
 - **exit** never fails
 - command line arguments are transferred as **strings**
 - `argv[argc]` is a _null pointer_

## chapter 8 - c library functions
-- -
`__STDC_WANT_LIB_EXT1__` and `__STDC_WANT_LIB_EXT1__`
- identifier names terminating with `_s` are reserved
- opaque types are specified through functional interfaces.
- don't rely on implementation details of opaque types.
- text i/o converts data
- trailing arguments exist
- use `%b` and `%x` to print bit patterns
- don't use `gets`
- [ ] learn what assertions in c are.
