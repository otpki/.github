# otpki/.github

Organization-wide GitHub configuration for OTPKI. This repository is the source
of truth for shared community health files, issue and pull request templates,
reusable CI workflows, and starter workflow templates.

## What lives here

| Path                                                                 | Purpose                                                                                                          |
| -------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `profile/README.md`                                                  | Public organization README                                                                                       |
| `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`, `SUPPORT.md` | Community health defaults for repos without their own                                                            |
| `CODEOWNERS`                                                         | Org-wide default code owners (`@otpki/dev-team`)                                                                 |
| `ISSUE_TEMPLATE/`, `PULL_REQUEST_TEMPLATE.md`                        | Default templates for repos without their own                                                                    |
| `.github/workflows/reusable-*.yml`                                   | Reusable workflows called by other repos                                                                         |
| `.github/actions/setup-ci/`                                          | Shared Go + aqua + Just setup action (`otpki/.github/.github/actions/setup-ci@v1`)                               |
| `.github/actions/tool-versions/`                                     | Reads `versions.json` and exposes each tool as an output                                                         |
| `.github/actions/docker-build-image/`                                | Build + push one image with org-standard metadata, tags, secrets, and cache                                      |
| `.github/actions/trivy-gate-verdict/`                                | Trivy warn/enforce gate                                                                                          |
| `workflow-templates/`                                                | Starter workflows shown under Actions -> New workflow                                                            |
| `templates/`                                                         | `labels.yml` + `release.yml` synced by `label-sync.yml`/`release-sync.yml`. `trivy.yaml` is the org Trivy policy |
| `renovate.json`                                                      | Shared Renovate config, repos extend `github>otpki/.github:renovate.json`                                        |

## Reusable workflows

Callers pin to the `v1` tag. Repos define their own triggers and call:

```yaml
jobs:
  check:
    uses: otpki/.github/.github/workflows/reusable-go-check.yml@v1
    with:
      commands: |
        just format-check
        just lint
        just test-ci
        just tidy
```

| Workflow                         | Use                                                                                                                                                                                                                    |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `reusable-go-check.yml`          | Checkout, Go, Just, aqua tools, then caller-supplied check commands plus a clean-tree gate and optional advisory govulncheck                                                                                           |
| `reusable-codeql.yml`            | CodeQL analysis, pass a JSON `languages` matrix and optional `build-commands` for manual build-mode                                                                                                                    |
| `reusable-fast-forward.yml`      | `/fast-forward` PR comment merge (callers grant write permissions and gate on `issue_comment`)                                                                                                                         |
| `reusable-dependency-review.yml` | PR dependency review for vulnerable or "denied-license" packages                                                                                                                                                       |
| `reusable-container-check.yml`   | Per-arch local image build + Trivy scan (warns on PRs, fails CRITICAL/HIGH on tags, secrets always fail). Optional `pre-build-commands`/`pre-build-artifacts` share built assets (ex. theme JARs) with the image build |
| `reusable-actionlint.yml`        | actionlint + zizmor over `.github/`, for repos that lint their own workflows on PRs                                                                                                                                    |
| `reusable-docker-publish.yml`    | Multi-arch image publish. Per-arch native builds pushed by digest and Trivy-scanned under the bundled org policy. A manifest job then applies tags, optional ghcr.io mirror, cosign signatures + SBOM                  |

## Global tool versions

`versions.json` at this repo's root pins the org toolchain. Bump it in a PR
and every CI run across the org picks it up.

```json
{ "go": "1.27.3", "node": "26.13.0" }
```

## Per-repo overrides

A repository's own community health files always win. A repo with its own
`SECURITY.md`, templates, or `CONTRIBUTING.md` uses those instead of the
defaults here. Forks (circl, pkcs7, scep) intentionally keep their upstream
workflows and files.
