---
title: Generics
---

Since C doesn't have any generic support out-of-the-box, it is 
recommended to create functions that use type `void*` or any alias of it
in place where generic type could be used (additionally type size may 
be supplied for certain operations).

To allow end users use concrete types, it is recommended to provide
macros that generate corresponding inlined functions, for example:

```c
ayte_array_t* ayte_array_set(ayte_array_t* subject, void* value);
void* ayte_array_get(ayte_array_t* subject, size_t index);

# define __TOKEN(x) x
# define AYTE_ARRAY_GENERATE_INTERFACE(name, type) \
    inline ayte_array_t* ayte_array_set_ ## name (ayte_array_t* subject, __TOKEN(type) value) { \
        return ayte_array_set(subject, (void*) value); \
    } \
    \
    inline type ayte_array_get_ ## name (ayte_array_t* subject, size_t index) { \
        return (type) ayte_array_get(subject, index); \
    }
```


