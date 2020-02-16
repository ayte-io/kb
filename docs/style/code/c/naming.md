---
title: Naming
---

### Prefixing

All symbols must have an understandable prefix that is not prone to 
collisions. Generally it's recommended to use `ayte_<library name>_`,
substituting it with abbreviation in case of long name
(`Stream Processing` -> `asp_` or `ayte_sp_`); if library provides some 
universal symbols, like general-use types, they may be prefixed with
`ayte_` only.

Library *should* provide unprefixed version of types as well, so end 
users, if they're sure that won't cause collisions, could use simplified
interface:

```c
// ayte/standard/collection/array.h

typedef struct {
  void* content;
  size_t length;
  size_t element_size;
} ayte_array_t;

ayte_array_t* ayte_array_allocate(size_t length, size_t element_size) {
    // ...
}

// ayte/standard/collection/array/@stripped.h

typedef array_t ayte_array_t;

array_t* array_allocate(size_t length, size_t element_size) {
    return ayte_array_allocate(length, element_size);
}
```

It is recommended to use `@stripped.h` name for file placed in directory
named after unit name (as shown above) for such definitions. `inline` 
keyword should not be used, because that may add unnecessary complexity
for debugging non-optimized code, and compilers should do that 
optimization automatically.

### Include guards

Include guards must be named after file location in upper case, 
substituting all invalid characters (slashes and dots) with underscore.
Combined with file naming requirements, this will automatically generate
unique constant, which won't case collisions.

### Macros

Macros should be named in upper case using underscores instead of
whitespaces, specify clear description of their purpose in their name,
and prefixed in usual 
`AYTE_<library name>_<optional module name>_<macro name>` style:

```
# define AYTE_STREAM_PROCESSING_PUBLISHER_GENERATE_INTERFACE(TYPE_NAME, TYPE) \
  inline ayte_publisher_t* ayte_ ## TYPE_NAME ## _publisher_allocate() { \
    return ayte_publisher_allocate(sizeof( TYPE )); \
  }
```
