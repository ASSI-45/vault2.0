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