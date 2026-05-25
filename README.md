# XPScerpto

XPScerpto is a governed sovereign cryptographic infrastructure platform.

It is designed around explicit authority, controlled module boundaries, fail-closed behavior, evidence-backed validation, and conservative claim discipline. XPScerpto is not organized as a loose collection of cryptographic utilities. It is structured as a governed platform where execution authority, validation evidence, and public claims must remain aligned.

Official project information may be available at:

```text
https://xpscerpto.eu
```

GitHub organization:

```text
https://github.com/xpscerpto
```

## Current status

XPScerpto is under active sovereign validation and hardening.

This repository must not be described as production-ready unless the required validation gates prove that status through live evidence.

Conservative global claim boundaries remain in force unless the relevant acceptance gates prove otherwise:

```text
PRODUCTION_READY = NO
FULL_SANITIZER_CTEST_CLAIMED = NO
FULL_GRAPH_ACCEPTED = NO
```

Subsystem-specific boundaries remain scoped to their own gates. Examples include:

```text
FHE_PRODUCTION_READY = NO
FHE_BOOTSTRAP_COMPLETE = NO
```

These flags are not marketing language. They are claim boundaries. They protect the repository from accidental overclaim, stale evidence, partial validation, and misleading release status.

## What XPScerpto is

XPScerpto is a cryptographic infrastructure project with a governance-first architecture.

It focuses on:

- explicit execution authority;
- platform-controlled admission;
- hardware evidence and routing discipline;
- authority-routed SIMD execution;
- cryptographic domain separation;
- FHE, BFV, CKKS, and bootstrap validation discipline;
- strict module boundaries;
- fail-closed behavior;
- evidence-backed testing;
- CI validation gates;
- review and ownership discipline;
- documentation that does not outrun evidence.

The project’s engineering model is based on the principle that correctness, authority, evidence, and claims must describe the same truth.

## What XPScerpto is not

XPScerpto is not:

- a normal utility library;
- a collection of unrelated crypto snippets;
- a production-ready claim by default;
- a project where build success implies acceptance;
- a project where sanitizer configuration implies sanitizer cleanliness;
- a project where target-only success implies full graph truth;
- a project where one subsystem’s progress implies platform-wide readiness.

Every acceptance claim must be proven by the relevant gate.

## Core authority chain

The expected authority flow is:

```text
platform governance
→ platform.api
→ hardware authority
→ routing capsule
→ domain execution
→ audit and evidence
```

Domain code must not invent execution authority by probing the operating system, CPU, compiler environment, hidden runtime state, or local capability shortcuts.

A capability may exist on a machine, but that does not make it admitted execution authority.

## Core validation discipline

XPScerpto keeps validation levels separate:

```text
configure success ≠ build success
build success ≠ test success
test success ≠ sanitizer truth
target success ≠ full graph truth
subsystem success ≠ repository-wide acceptance
```

This distinction is central to the repository.

A precise partial result is acceptable. A broad claim without matching evidence is not.

## Documentation map

Start here:

```text
START_HERE.md
```

Recommended reading order:

1. `START_HERE.md`
2. `GOVERNANCE.md`
3. `ENGINEERING_PRINCIPLES.md`
4. `AUTHORITY_MODEL.md`
5. `ARCHITECTURE.md`
6. `MODULE_BOUNDARIES.md`
7. `THREAT_MODEL.md`
8. `SECURITY.md`
9. `CI_VALIDATION_GATES.md`
10. `REVIEW_POLICY.md`
11. `CONTRIBUTING.md`
12. `OWNERSHIP_MODEL.md`
13. `CODEOWNERS`
14. `SUPPORT.md`

Each document has a distinct role. They should not be collapsed into one generic README.

## Document roles

| Document | Role |
|---|---|
| `START_HERE.md` | Entry point and reading order |
| `GOVERNANCE.md` | Decision authority, claim discipline, and protected-surface governance |
| `ENGINEERING_PRINCIPLES.md` | Engineering discipline and implementation philosophy |
| `AUTHORITY_MODEL.md` | Source and flow of execution authority |
| `ARCHITECTURE.md` | Repository-wide system structure |
| `MODULE_BOUNDARIES.md` | Import boundaries, public surfaces, and protected ownership |
| `THREAT_MODEL.md` | Assets, trust boundaries, adversaries, and threat mapping |
| `SECURITY.md` | Vulnerability reporting and security-sensitive change policy |
| `CI_VALIDATION_GATES.md` | Validation gates and evidence requirements |
| `REVIEW_POLICY.md` | How reviewers evaluate changes |
| `CONTRIBUTING.md` | How contributors prepare changes |
| `OWNERSHIP_MODEL.md` | Platform-neutral ownership policy |
| `CODEOWNERS` | GitHub-specific review routing |
| `SUPPORT.md` | General support process and public-support boundaries |

## Repository architecture

At a high level, XPScerpto is organized around layered responsibility:

```text
governance and policy documents
  ↓
build and CI policy
  ↓
base layer
  ↓
platform layer
  ↓
platform.api admitted surface
  ↓
hardware authority layer
  ↓
routing and dispatch layer
  ↓
audit and evidence layer
  ↓
domain execution layers
  ↓
tests, tools, and release evidence
```

Major repository families may include:

- `base` — foundational types, checked primitives, and low-level policy anchors;
- `platform` — platform root, provider admission, runtime policy, and operating boundary;
- `platform.api` — admitted platform-facing surface;
- `hw` — hardware evidence, topology, capability interpretation, and routing support;
- `simd` — authority-routed acceleration and data movement;
- `FHE` — homomorphic encryption, BFV, CKKS, bootstrap, key switching, NTT/RNS, and FHE surface guards;
- `hash`, `kdf`, `mac`, `aead`, `aes` — symmetric cryptographic domains;
- `pqc`, `ed25519`, `x25519`, `rsa` — asymmetric and post-quantum cryptographic domains;
- `number`, `atomic`, `memory`, `integrity` — support layers for arithmetic, synchronization, memory, and integrity behavior;
- `audit` — evidence, ledgers, and attestation-related behavior;
- `tests` — validation, regression, negative tests, authority tests, and sanitizer-backed testing;
- `tools` — scans, replay utilities, evidence support, and CI helpers;
- `docs` — normative and explanatory documentation.

This map describes architectural role, not production-readiness status.

## Protected surfaces

The following areas are protected by default:

```text
include/xps/crypto/base/
include/xps/crypto/platform/
include/xps/crypto/platform.api/
include/xps/crypto/hw/
include/xps/crypto/simd/
include/xps/crypto/FHE/
include/xps/crypto/hash/
include/xps/crypto/kdf/
include/xps/crypto/mac/
include/xps/crypto/aead/
include/xps/crypto/aes/
include/xps/crypto/pqc/
include/xps/crypto/ed25519/
include/xps/crypto/x25519/
include/xps/crypto/rsa/
include/xps/crypto/number/
include/xps/crypto/atomic/
include/xps/crypto/memory/
include/xps/crypto/integrity/
include/xps/crypto/audit/
CMakeLists.txt
tests/
tools/
docs/
.github/
```

Changes to protected surfaces require clear scope, appropriate review, and evidence.

Protected surfaces must not be changed through hidden shortcuts, weakened tests, deleted assertions, fake fallbacks, metadata-only proofs, or production overclaims.

## Build and validation

Build and validation details may vary by platform, compiler, generator, and configured options.

Use the repository’s current build system and CI documentation as the source of truth for commands. When reporting build or test results, include the exact commands and scope.

Validation claims should identify:

- source tree or commit;
- compiler and version;
- CMake version;
- generator;
- build configuration;
- commands executed;
- tests run;
- sanitizer configuration and runtime status, if claimed;
- failures or skipped tests;
- exact blocker, if incomplete.

Do not report a validation claim without enough evidence to support it.

## Security

Do not report vulnerabilities through public issues, pull requests, discussions, public website forms, or social media posts.

Use:

```text
SECURITY.md
```

for vulnerabilities and security-sensitive reports.

Security-sensitive topics include:

- secret key or private key exposure;
- seed, token, credential, or secret material leakage;
- cryptographic correctness failures with security impact;
- authority bypasses;
- platform or provider bypasses;
- unauthorized hardware routing or SIMD dispatch;
- memory safety findings in protected paths;
- CI, evidence, or release manipulation;
- documentation claims that could mislead users about security or readiness.

If unsure whether an issue is security-sensitive, treat it as security-sensitive.

## Support

For non-security questions, use:

```text
SUPPORT.md
```

Support topics may include:

- build help;
- installation help;
- non-security bug reports;
- documentation clarification;
- test execution questions;
- contribution workflow questions.

Do not include secrets, private keys, tokens, exploit details, private data, or active vulnerability reproduction steps in public support channels.

## Contributing

Contributions are welcome when they are clear, scoped, and evidence-backed.

Before contributing, read:

```text
CONTRIBUTING.md
REVIEW_POLICY.md
MODULE_BOUNDARIES.md
CI_VALIDATION_GATES.md
SECURITY.md
```

A pull request should explain:

- what changed;
- why it changed;
- which surfaces are affected;
- whether protected surfaces are touched;
- whether the change is security-sensitive;
- what tests were run;
- what evidence supports the claim;
- what was not run;
- what blockers remain;
- what claims are not being made.

Do not open a public pull request with vulnerability details unless disclosure has been coordinated under `SECURITY.md`.

## Ownership and review routing

Ownership policy is defined in:

```text
OWNERSHIP_MODEL.md
```

GitHub review routing is implemented by:

```text
CODEOWNERS
```

`CODEOWNERS` is platform-specific. It routes review requests in GitHub. It does not replace the platform-neutral ownership policy or the review discipline defined in `REVIEW_POLICY.md`.

A change may have the required owners and still be rejected if it violates governance, authority, boundaries, validation, evidence, or claim discipline.

## Claim boundaries

The following kinds of claims require evidence from the relevant gates:

- production-ready;
- production-grade;
- deployment-ready;
- full graph passed;
- sanitizer clean;
- security hardened;
- fully validated;
- release accepted;
- subsystem accepted;
- FHE accepted;
- CKKS accepted;
- BFV accepted;
- bootstrap complete;
- full runtime closure;
- full materialization closure.

Equivalent or stronger claims are also covered.

Do not make these claims unless the relevant acceptance gate proves them through live evidence.

## License

License status: not yet selected.

XPScerpto is currently published for review, evaluation, and project visibility only. No permission is granted to use, copy, modify, redistribute, sublicense, or commercially deploy the code unless a license is later published or written permission is granted by the project owner.

## Final note

XPScerpto should be evaluated as a governed cryptographic infrastructure system.

Its credibility depends on alignment between:

```text
implementation
authority
tests
evidence
documentation
claims
```

The project advances only when those dimensions describe the same truth.
