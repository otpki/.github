# Contributing to OTPKI

Thanks for your interest in contributing. This guide applies to OTPKI
repositories that do not have their own `CONTRIBUTING.md` — check the
repository first and follow its local guide when one exists.

## Before you start

- For bugs, file an issue with a minimal reproduction. For features, open an
  issue to discuss the approach before writing code. Substantial API or
  behavior changes are easier to land when the design is agreed first.
- Do not file suspected vulnerabilities as public issues. See
  [SECURITY.md](https://github.com/otpki/.github/blob/main/SECURITY.md).
- Most repositories use the issue templates and pull request template provided
  by this organization. Filling them out completely is the fastest way to a
  review.

## Development conventions

- Go repositories pin their toolchain in `go.mod` and their dev tools in
  `.aqua.yaml` where present. A `Justfile` provides the standard entry points:
  `just format`, `just lint`, `just test`, and `just check`. Run `just check`
  (or the closest equivalent) before opening a PR — CI enforces it.
- Keep changes focused. One PR should do one thing.
- Add or update tests for changed behavior. Cryptographic changes should cite
  specifications or include test vectors.
- Update docs and examples when behavior visible to users changes.
- Preserve existing copyright, license, and attribution notices, especially in
  forked repositories.

## Pull requests

- Fill in the PR template: what changed, why, and how it was verified.
- Keep the working tree clean. CI fails if generation, formatting, or
  `go mod tidy` leaves changes.
- Comment `/fast-forward` on your own PR to fast-forward merge it once checks
  are green, where that workflow is enabled.

## License

Unless a repository states otherwise, contributions are licensed under the
repository's license (Apache-2.0 for OTPKI-authored projects, upstream license
terms preserved in forks).
