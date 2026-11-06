# ChronitonDB security tracker

This repository holds the public VEX statements of [ChronitonDB](https://github.com/chronitonlabs/chronitondb). For each known vulnerability in a library ChronitonDB ships, they say whether each supported line is affected, and what to do about it.

VEX means Vulnerability Exploitability eXchange. A vulnerability scanner lists every CVE in every library it finds. A VEX statement adds what the scanner cannot know: whether the vulnerable code is shipped, reachable or fixed in ChronitonDB. The statements use the [OpenVEX](https://github.com/openvex/spec) 0.2.0 format, which many scanners read directly.

This follows the practice of the Debian security tracker and the Ubuntu CVE tracker: one public place, updated as vulnerabilities are found, not only at release time.

## What is here

One OpenVEX document per supported line:

| File | Line |
|---|---|
| `vex/chronitondb-5.0.openvex.json` | ChronitonDB 5.0 |
| `vex/chronitondb-6.0.openvex.json` | ChronitonDB 6.0 |

Each statement names:

- the vulnerability, by its CVE id
- the product, as a package URL: the line, `pkg:github/chronitonlabs/chronitondb@chronitondb-5.0`, or one release, such as `pkg:github/chronitonlabs/chronitondb@5.0-chronitondb3`
- the library, as a package URL, when the vulnerability is in a library ChronitonDB ships
- one status

## What each status means

| Status | Meaning | What comes with it |
|---|---|---|
| `not_affected` | The vulnerable code is not shipped, not reachable, or needs a configuration ChronitonDB does not allow | A justification and the evidence: the library list, the missing class, or the call path |
| `affected` | The line or release carries the vulnerability | What to do: the release to move to, or a workaround until one exists |
| `fixed` | A release carries the fix | That release |
| `under_investigation` | The check is not finished | Replaced within 5 business days, the triage time in the security policy |

## How to use it

- Point a scanner that reads OpenVEX at the document of your line, so findings that do not apply to ChronitonDB drop out of its report.
- Read a document's history with `git log` to see when a statement changed.
- Every ChronitonDB release also ships the line's VEX document as it stood at release time, next to its SBOM.

## How it is kept

The security engineer checks the libraries of each supported line every day and proposes changes here by pull request, at most one a day. Each pull request is reviewed and then merged by a ChronitonDB maintainer. Every commit on `main` is signed.

## What is never here

- Anything about a vulnerability in ChronitonDB's own code before its advisory is published.
- A reporter's name, exploit details, or a private triage report.

## Reporting a vulnerability

Never in an issue, pull request or discussion here. Report it privately through the ChronitonDB repository: open its **Security** tab and choose **Report a vulnerability**. The full policy, with response times and how disclosure is coordinated with the Apache Cassandra project, is in [security.md](https://github.com/chronitonlabs/chronitondb/blob/chronitondb-5.0/docs/process/security.md).

## More

- [Security policy](https://github.com/chronitonlabs/chronitondb/blob/chronitondb-5.0/docs/process/security.md)
- [Compliance: SBOM and VEX](https://github.com/chronitonlabs/chronitondb/blob/chronitondb-5.0/docs/process/compliance.md)
- [Release outputs](https://github.com/chronitonlabs/chronitondb/blob/chronitondb-5.0/docs/process/release.md)

## Licence

The statements in this repository are licensed under the [Apache License 2.0](LICENSE), the same licence as ChronitonDB.
