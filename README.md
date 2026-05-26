[update-readmes]   Mode: rewrite — migrating to template structure...
# create-gonode

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/create-gonode)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/create-gonode.git
cd create-gonode
```

## Usage


### 1. Write Your Go Code

```go
// mylib.go
package mylib

func Add(a, b int) int {
    return a + b
}

func Greet(name string) string {
    return "Hello, " + name + "!"
}
```

### 2. Export to JavaScript

```go
// src/node/exports.go
//go:build js

package main

import (
    "github.com/user/mylib"
    "github.com/gopherjs/gopherjs/js"
)

func main() {
    js.Module.Get("exports").Set("add", mylib.Add)
    js.Module.Get("exports").Set("greet", mylib.Greet)
}
```

### 3. Create TypeScript Entry

```typescript
// src/node/index.ts
import * as lib from "./lib.js";

export const add: (a: number, b: number) => number = lib.add;
export const greet: (name: string) => string = lib.greet;
```

### 4. Build

```bash
pnpm run build
```

### 5. Use in Node.js

```typescript
import { add, greet } from "my-go-module";

console.log(add(2, 3));        // 5
console.log(greet("World"));   // Hello, World!
```

## Configuration


### package.json exports

```json
{
  "exports": {
    "./node": {
      "types": "./dist/node/index.d.ts",
      "import": "./dist/node/index.mjs"
    },
    "./browser": {
      "types": "./dist/browser/index.d.ts",
      "import": "./dist/browser/index.js"
    }
  }
}
```

### tsdown.config.ts

```typescript
import { defineConfig } from "tsdown";

export default defineConfig([
  {
    entry: "src/node/index.ts",
    format: "esm",
    outDir: "dist/node",
    platform: "node",
    dts: true,
  },
  {
    entry: "src/browser/index.ts",
    format: "esm",
    outDir: "dist/browser",
    platform: "browser",
    dts: true,
  },
]);
```

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/create-gonode`](https://github.com/Interested-Deving-1896/create-gonode) and mirrored through:

```
Interested-Deving-1896/create-gonode  ──►  OpenOS-Project-OSP/create-gonode  ──►  OpenOS-Project-Ecosystem-OOC/create-gonode
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
<!-- License not detected — add a LICENSE file to this repo. -->
<!-- AI:end:license -->
