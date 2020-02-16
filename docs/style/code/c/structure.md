---
title: Structure
---

### Location

All files must reside within directory of pattern 
`ayte/<library-name>/<library module if library is separated>/<version>`, e.g.
`ayte/stream-processing/0.1` or `ayte/consensus/paxos/0.2`, except for header 
that exposes complete library / module functionality (which must have 
the same name as directory suffixed by `.h`). This must be done to 
completely eliminate possibility of collisions with files from other 
projects, distinguish system libraries from auxiliary libraries and 
provide end user way of understanding what's actually referenced just 
by looking at `#include`s. Following example demonstrates this:

```c
# include <stddef.h>
# include <ayte/stream-processing/publisher.h>
# include <ayte/consensus/paxos.h>
```

### Naming

Files names must not be shortened and should contain complete name of 
exposed unit, even if it's long. If unit is a particular implementation
of an entity described by parent directory, it should be omitted:

```
ayte/stream-processing/publisher.h

// but

ayte/standard/tree/b.h
```

It is recommended to name files in lower case with whitespaces replaced
by hyphens: `ayte/stream-processing.h`.

In case of files that expose different functionality rather than 
specific unit should be prepended by `@`. Rationale for using that 
symbol is that nearly every other ASCII symbol either prohibited for
usage on some platforms or used in native shell syntax.

```
ayte/stream-processing/@quirks.h
```

### Separation

Instead of having large files that expose everything at once, use 
small files that provide interface of single logical unit only, and
collect them with a header file (that includes all lower-level headers)
at parent level:

```
tree/b.h
tree/b.c
tree/red-black.h
tree/red-black.c
tree/radix.h
tree/radix.c
tree.h
```

```c
// tree.h

#include "tree/b.h"
#include "tree/red-black.h"
#include "tree/radix.h"
```

With that approach end user may both select only necessary types or all
of them at once.
