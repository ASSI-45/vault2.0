# the basics for elixir

Run esx in the terminal to open an interactive interpeted session in elixir.
Pres C-c twice to **exit**.

## nvim
Use lexical in Mason and don't forget...
```
TSInstall elixir
```

Mix is the build tool for elixir.
It does these things.
1. Build projects
2. Compile projects
3. Run projects

To generate a project run.
```bash 
mix new <project>
````

## hex
Hex is Elixir's package management tool. Just like npm or pip.
You can go to there [website](https://hex.pm/) for packages and just copy the right on one into you'r **_mix.esx_** "config".
in the deps section, between the []. But first youl need to install **hex**, by running this command.

```bash
mix local.hex
```

Now to install the dependentie's youl need to run.
```bash
mix deps.get
```

# the language

Now we will start taking about types i think... Wow (this is my first time to).

## variables and others
In elixir we call what we call variable declarations in other languages, bindings in Elixir.

Just like this.
```elixir
x = 5
```

Dont be fooled by the `=`. Its actualy something else we will cover over.

### "cosntants"
we cant do it like in javascript.
```javascript
cosnt x = 5;
```

But instead we have a "workaround". By cowing in to the module section of our Elixir program and defing are sudo const with.
```elixir
@x 5
```
These are called module attributes.

### strings
You define a string by using double quotes in your program.
```elixir
"hello"
````

You can use escape charcter like \n or \t in a tring. 

**_Note!_**: That `IO.puts()` already puts a new character at the end of the line.

You can also use unicode charcters in side of a string or in iex. By using a `?` character. This will return its code point.

```elixier
?a
```
Will return `97`.

You can use code [Code points](https://codepoints.net/?lang=en) website to see the hex or decimal value of a specif character.


Use these when getting a value from the user.

### atoms

Atoms are like strings but constant. These are usefull for when youll be needing a small or any type of world list through out your application. Think of lexer.

**atom**
```elixir
:hello
````

The value itself is the same as a string.

**_Note!:_** That a atom for static values is more beneficial for preformance in Elixir. Because the language just needs to check the memory location instead of each charachter in the string.

If you have a space in your atom do this.
```elixir
:"hello world"
```

### compount types
These are types that consist of basic types. To make more complex types.

#### tuples
A tuple may contain elements of different types, which are stored contiguously in memory. Accessing any element takes constant time, but modifying a tuple, which produces a shallow copy, takes linear time. Tuples are good for reading data while lists are better for traversals.

```elixer
price = {1, 2, 5}
```

**_Note!_**: You can also destructure them.

#### lists
Lists are collections of values which may include multiple types; lists may also include non-unique values.

```elixir
[3.14, :pie, "Apple"]
```

Its faster to **prepent** to a list then to **append** to list

#### maps
Maps store **_key value pairs_**. Usefull for lookup tables. You define one as such.

```elixir
memberships = %{
  Premium: 30,
  Standerd: 20,
  Cheap: 10,
}
```

You can acces them as such.

```elixir
memberships.Premium  # map_name.map_element
```

#### structs
Structs are like maps and build on top of them. But bring
default values and pre-compile checks.

```elixir
defmodule User do
  defstruct name: "John", age: 27
end
```


## controll flow

### the if and else statement

```elixer
if status === :gold do
      IO.puts("Welcome to the cool lounge, #{name}")
    else
      IO.puts("Your not in the cool lounge, #{name}")
end 
```

