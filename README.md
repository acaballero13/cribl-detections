# cribl-detections

Managed-detection format repo for [Cribl Intel Hub](https://github.com/acaballero13/cribl-intel-hub).

Each detection is one YAML file carrying the canonical Cribl Search KQL query,
preserved upstream metadata (severity, description, tactics, `catalogProvenance`),
and a divergence baseline — human-diffable so changes review like code.

## How this repo gets populated

This is the **versioned tier** of the Intel Hub detection lifecycle:

```
Draft / Testing  →  Curated (this repo)  →  Production (Cribl Search saved searches)
   (KV-only)         (committed YAML)             (scheduled, live)
```

Detections land here through the **Commit** action on a Workbench detection in
the Intel Hub UI. The first commit scaffolds the repo structure if it's empty;
the app is a git *client*, never a host. After a detection is committed, its
`status` flips to `curated` and it appears in **My Library**.

## Reviewing changes

YAML-per-detection means every change is a focused diff: a query tweak, a
severity bump, a retagging. Open a PR, review the diff, merge — same workflow
as code review.

## License and attribution

Imported detections preserve their upstream license through
`catalogProvenance.licenseId`:

- **SigmaHQ Core** rules under the [Detection Rule License 1.1](https://github.com/SigmaHQ/Detection-Rule-License).
- **Splunk ESCU** and **MITRE CAR** under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

User-authored detections in this repo have no upstream license attached.
