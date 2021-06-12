---
title: Organization
---

### Translation Units

Each `.ts` file should contain same-named namespace, type or class:

```typescript
// Names.ts
export namespace Names {
    export function isName(input: any): boolean {
        return typeof input === 'string';
    }
}
```

```typescript
// IFunction.ts
export type IFunction<T, U> = (value: T) => U; 
```

```typescript
export class Set<T> {
    private readonly values: T[];

    public constructor(...values: T[]) {
        this.values = values;
    }

    public contains(value: T): boolean {
        return this.values.indexOf(value) > -1;
    }
}
```

Each `.tsx` file should contain one component expressed as class

```typescript jsx
import React, {Component} from 'react';

export class HelloWorld extends Component<{}, {}> {
    public render() {
        return <span>Hello world!</span>;
    }
}
```

#### Nesting

### Repository structure

#### Monorepo

src/
dist/
workspace/
