---
title: Filesystem Organization
---

### Package structure

Minimal package should consist of following elements:

- package.json
- src: directory with source code files
- dist: a non-committed directory for build artifacts

#### /src/

Sources directory should contain only TypeScript source code files and
resource files, which may be anything that is needed in runtime.

Source code files must be named after enclosed symbol, classes / 
namespaces for `.ts` files and components for `.tsx` files:

```typescript jsx
// Button/Shutdown.tsx
import React, {Component} from 'react';

export class Shutdown extends Component<{}, {}> {
    
}
```

#### /dist/

### UI

### Repo: multirepo, monorepo
