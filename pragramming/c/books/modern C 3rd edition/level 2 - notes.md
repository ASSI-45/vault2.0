-- -
This chapter should allow you to write pro level c code.
## chapter 9 style
-- -
- pick a consistent strategy for white pace and other text formating
- `astyle` is a formating tool
- chose consistent naming scheme
### reserved names
- names starting with an underscore and a second underscore or capital letter are reserved for language extensions and other internal use.
- Names starting with an are reserved for file scope identifiers and **enum**, **struct** and **union** tags
- Macros have all-caps names
- all identifiers that have predefined meaning are reserved and cannot be used in file scope. -> all functions in the c library, identifiers starting with _str_, starting with _E_, ending with an _t

 - don't pollute the global space of identifiers

## chapter 11
-- -
 