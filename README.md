# kerml

A compact, idiomatic Go implementation of the KerML kernel.  
This package provides a minimal semantic core for building modeling tools, language adapters, and persistence layers that rely on a small, well‑defined kernel.

---

## Overview

**kerml** implements the canonical kernel primitives used as a semantic foundation for modeling languages.  
The package focuses on a small, stable API surface: identity, core element interfaces, a lightweight expression AST and evaluator, and a pluggable store abstraction.  
The kernel is intentionally minimal so downstream packages can remain thin and focused.

---

## Key Features

- **Stable identity** utilities with UUID/URN generation and canonical equality semantics.
- **Core interfaces** for `Element`, `Type`, `Feature`, and `Relationship`.
- **Expression core** with a small AST and evaluator suitable for constraints and derived values.
- **Pluggable store** interface and an in‑memory reference implementation for fast iteration.
- **Deterministic mapping points** for AST to kernel element conversion used by parsers and importers.

---

## Package Layout

```
/euginwae2/kerml
  ├─ id.go            // ID type and utilities
  ├─ element.go       // Element, Type, Feature interfaces
  ├─ expr
  │   ├─ ast.go       // expression AST nodes
  │   └─ eval.go      // evaluator and runtime
  ├─ store
  │   ├─ store.go     // Store interface
  │   └─ memstore.go  // in-memory reference store
  ├─ validate.go      // kernel-level validators
  └─ examples         // small usage examples and tests
```

**Package responsibilities**

- **euginwae2/kerml** exposes the kernel public API and core semantics.
- **euginwae2/kerml/expr** contains the expression AST and evaluator used by constraints.
- **euginwae2/kerml/store** defines the `Store` interface and ships a `memstore` for development and tests.
- **examples** contains round‑trip and unit examples that exercise kernel semantics.

---

## Minimal API Examples

```go
// pkg/kerml/id.go
package kerml

type ID string

func NewID() ID {
    // returns a UUID v4 based ID as a string
}
```

```go
// pkg/kerml/element.go
package kerml

type Element interface {
    ID() ID
    Name() string
    Kind() string
}
```

```go
// pkg/kerml/store/store.go
package store

import "github.com/yourorg/kerml/pkg/kerml"

type Store interface {
    Put(e kerml.Element) error
    Get(id kerml.ID) (kerml.Element, error)
    Query(q Query) ([]kerml.Element, error)
    Begin() (Transaction, error)
}
```

---

## Installation

Add the package to your module:

```bash
go get github.com/euginwae2/kerml@v0.0.0
```

Run tests locally:

```bash
git clone https://github.com/euginwae2/kerml.git
cd kerml
go test ./...
```

---

## Quick Start Example

```go
package main

import (
    "fmt"
    "github.com/euginwae2/kerml/pkg/kerml"
    "github.com/euginwae2/kerml/pkg/kerml/store"
)

func main() {
    s := store.NewMemStore()
    e := &kerml.BasicElement{
        ID:   kerml.NewID(),
        Name: "KernelElement",
        Kind: "Element",
    }
    _ = s.Put(e)
    got, _ := s.Get(e.ID())
    fmt.Println("Stored element:", got.Name())
}
```

---

## Development and Roadmap

**Development workflow**

- Keep the kernel API small and stable.
- Write unit tests for every kernel primitive and evaluator rule.
- Use the `memstore` for fast iteration and add SQL adapters when persistence is required.

**Planned milestones**

- **v0.1** Minimal kernel types, memstore, expression AST, and unit tests.
- **v0.2** Expression evaluator improvements, JSON serialization, and basic validators.
- **v1.0** Stable kernel API, SQL store adapter, and documented examples.

---

## Contributing

**How to contribute**

- Fork the repository and open pull requests against `main`.
- Include tests for new features and follow idiomatic Go patterns.
- Keep changes scoped to kernel responsibilities and avoid leaking higher‑level semantics into the kernel.

**Repository policies**

- Use feature branches and descriptive commit messages.
- CI runs `go test`, `golangci-lint`, and `go vet` on every PR.
- Maintain backward compatibility for public kernel APIs where possible.

---

## Commands

- **Run tests**: `go test ./...`
- **Run linters**: `golangci-lint run`
- **Build**: `go build ./...`

---

## License

This project is released under the **Apache 2.0** license. See the `LICENSE` file for details.

---

## Contact

For questions, issues, or contribution discussions open an issue in the repository or submit a pull request.
