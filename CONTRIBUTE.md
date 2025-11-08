**This CONTRIBUTING guide explains how to contribute code, tests, docs, and governance to the kerml repository and how we review and accept changes. Follow the steps below to get started quickly and make high‑quality contributions.**

### Purpose

kerml is a small, stable kernel package. This document describes the preferred workflow, code standards, testing expectations, and community norms to keep the kernel compact and reliable. Follow these guidelines to help maintain a consistent contributor experience and high code quality.

---

### Getting started

- **[Fork the repo](guide://action?prefill=Tell%20me%20more%20about%3A%20Fork%20the%20repo)**: Create a fork on GitHub and clone it locally.
- **[Create a branch](guide://action?prefill=Tell%20me%20more%20about%3A%20Create%20a%20branch)**: Use a descriptive branch name like `feat/expr-evaluator` or `fix/id-utils`.
- **[Open an issue first](guide://action?prefill=Tell%20me%20more%20about%3A%20Open%20an%20issue%20first)**: Discuss nontrivial changes before coding to avoid duplicated effort and align on design.
- **[Claim issues](guide://action?prefill=Tell%20me%20more%20about%3A%20Claim%20issues)**: Add a comment to indicate you are working on an issue and link your PR when ready.

---

### Contribution workflow

- **[Write tests](guide://action?prefill=Tell%20me%20more%20about%3A%20Write%20tests)**: Every feature or bugfix must include unit tests that exercise behavior and edge cases.
- **[Follow commit conventions](guide://action?prefill=Tell%20me%20more%20about%3A%20Follow%20commit%20conventions)**: Use clear, concise commit messages and reference issues in the body; follow the project’s commit style inspired by Go project practices.
- **[Open a pull request](guide://action?prefill=Tell%20me%20more%20about%3A%20Open%20a%20pull%20request)**: Target `main`, include a description, list changes, and attach test results.
- **[Respond to review](guide://action?prefill=Tell%20me%20more%20about%3A%20Respond%20to%20review)**: Address reviewer comments promptly and update the PR until it passes CI.

---

### Code style and testing

- **[Idiomatic Go](guide://action?prefill=Tell%20me%20more%20about%3A%20Idiomatic%20Go)**: Use standard Go patterns, keep packages small, and prefer interfaces for abstractions.
- **[Formatting and linting](guide://action?prefill=Tell%20me%20more%20about%3A%20Formatting%20and%20linting)**: Run `gofmt` and `golangci-lint` locally before pushing.
- **[Test coverage](guide://action?prefill=Tell%20me%20more%20about%3A%20Test%20coverage)**: Aim for meaningful coverage on core primitives and the expression evaluator.
- **[Deterministic behavior](guide://action?prefill=Tell%20me%20more%20about%3A%20Deterministic%20behavior)**: Kernel APIs must be deterministic and stable; avoid breaking public signatures without a major version bump.

---

### Review process and CI

- **[Automated checks](guide://action?prefill=Tell%20me%20more%20about%3A%20Automated%20checks)**: GitHub Actions runs tests, linters, and vet on every PR.
- **[Code review](guide://action?prefill=Tell%20me%20more%20about%3A%20Code%20review)**: At least one maintainer review is required for nontrivial changes; maintainers may request additional reviewers for core API changes.
- **[Merging](guide://action?prefill=Tell%20me%20more%20about%3A%20Merging)**: PRs merge after passing CI and receiving approvals; maintainers may squash or rebase as needed.

---

### Community and governance

- **[Code of conduct](guide://action?prefill=Tell%20me%20more%20about%3A%20Code%20of%20conduct)**: Be respectful and constructive in issues and PRs.
- **[License](guide://action?prefill=Tell%20me%20more%20about%3A%20License)**: Contributions are accepted under the repository license.
- **[Roadmap and issues](guide://action?prefill=Tell%20me%20more%20about%3A%20Roadmap%20and%20issues)**: Check the issue tracker and roadmap before proposing large changes.
