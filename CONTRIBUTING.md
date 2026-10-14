# Contributing to yol

## First issue

Look for
[`good first issue`](https://github.com/bilusteknoloji/yol/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)
labels. Each issue has a clear acceptance criterion and a size estimate.

## Development setup

```bash
# Go toolchain
go mod download

# Build binaries
go build ./cmd/yol

# Run yol tests
go test ./pkg/yol/... -v
```

## Documentation

`docs/` holds two kinds of content, and the distinction matters before you edit
anything there:

- `docs/adr/` are **hand-written and tracked**.
- `docs/api/` may be auto-generated API documentation.

## Architecture decision records

ADRs live in `docs/adr/`. Read them if any available before touching transport
or DX code.

## Commit style

Conventional commits: `feat(scope):`, `fix(scope):`, `chore(scope):`,
`docs(scope):`. Run checks before pushing — probably the pre-commit hooks
already enforces this.

## Code standards

- Go: `golangci-lint run ./...` must be clean. Each file in codebase must stay
  under 500 LOC.
- No `//nolint:` without a comment explaining why.
