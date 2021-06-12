---
title: Symbols
---

Following guidelines adhere to Google JavaScript style guide and 
TypeScript developers style guide with small changes.

### Variables

Variables and execution-local constants (i.e. declared inside functions)
should be declared as nouns using `camelCase`.

```typescript
const restrictiveSenderPolicy = 'v=spf1 -all';
```

It is recommended to explicitly specify types for variables whose type
is complex and isn't easily perceived after reading preceding code.

```typescript
type Transaction = {
    account: string;
    value: number;
}

function report(transactions: Transaction[]) {
    const totals: Record<string, number> = transactions.reduce((accumulator, transaction) => {
        const account = accumulator[transaction.account] || 0;
        accumulator[transaction.account] = account + transaction.value;
        return accumulator;
    }, {});

    return totals;
}
```

### Constants

Static constants declared outside of functions should be using uppercase
snake case (`ALL_CAPS`), whether they are exported or not. It is highly
recommended to always specify constant type, and if constant has complex
type that isn't easily perceived, it's absolutely necessary to specify 
it.

```typescript
const DEGREE: number = Math.PI / 180;

namespace Trigonometry {
    export const QUARTER_TURN: number = Math.PI / 2;
}

class Angle {
    public static readonly NORMALIZED_MAXIMUM: number = Math.PI;
    public static readonly NORMALIZED_MINIMUM: number = -Math.PI;
    // Reader would not easily understand what's going on if they would
    // see type as map of many numbers to other numbers.
    // So it's easier to explicitly state that it is number => number
    // mapping, especially given that more entries may arrive in future
    // and end user should work with this constant blindly.
    public static readonly PRECOMPUTED_VALUES: Readonly<Record<number, number>> = {
        0: 0,
        90: Math.PI / 2,
        180: Math.PI,
        270: -Math.PI / 2
    }
}
```

### Enums

Enums and enum members must be named as nouns. Enums must be named using
`PascalCase`, just as other enclosing symbols, while enum members must be
named using `UPPERCASE_SNAKE_CASE`, to be 


### Types & Namespaces

All types and namespaces should be named in PascalCase.

```typescript
interface ISerializer<T> {
    parse(serialized: string): T;
    write(value: T): string;
}

class NumberSerializer implements ISerializer<number>{
    public parse(serialized: string): number {
        return serialized ? parseFloat(serialized) : null;
    }                                 

    public write(value: number): string {
        return typeof value === 'number' ? value.toString() : null;
    }
}

namespace Parsers {
    export const NUMBER: ISerializer<number> = new NumberSerializer();
}
```

#### Interfaces

#### Methods and properties


#### Generic Parameters

Generic parameters should use single uppercase letter for name, possibly
followed by a number (`T`, `T1`, `T2` are all allowed names). It is
also recommended to use `T` name for generic parameter (unless it has 
very specific use, e.g. it makes sense to mark converter function as 
`C`), with following alphabet letters for additional parameters 
(`U`, `V`, `W`).

#### Aliasing
