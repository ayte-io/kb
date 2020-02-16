---
title: General
---

### Naming

Since C has only one flat namespace for everything, all symbols should 
be properly prefixed to avoid collisions. Same applies for files, so
there would be no chance of referencing wrong header while using `<>`
notation.

### Building

Except for very complex cases, all projects must not use anything 
besides standard toolchain for building the project.

Projects may freely use additional toolchains for tasks that are not
related to building, such as file generation (results of which are then
committed) or testing.

### Testing

#### Unit

Testing C is a pain. For every C project it is recommended to create 
bindings to any language and test it through framework of that language
to get wider set of assertions and smaller average time spent on single 
test.

#### Integration / E2E

Whenever library provides functionality that touches threading, 
inter-process communication, network communication, distributed tasks
and other functionality of similar complexity, it must also be tested
for conformity of such functionality, creating real usage examples
and stress-testing them. 
