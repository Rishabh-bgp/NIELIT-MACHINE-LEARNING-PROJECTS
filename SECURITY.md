# Security policy

This repository contains teaching notebooks and public sample tables. It does not run a service, store accounts, or ship a deployed model.

## Supported material

Security reports are relevant for:

- A credential, token, or private key committed by mistake.
- A notebook that instructs a reader to download or execute untrusted code without a warning.
- A dataset file that appears to contain personal data that should not be public.

A wrong accuracy score, a deprecated `load_boston` call, or a missing CSV is a normal bug. Open an issue for those.

## Reporting

Do not open a public issue for a suspected secret. Report it privately to the maintainer, Er. Rishabh Aryan, via GitHub, with:

- the file path and the commit, if you have it
- the kind of secret, not the secret itself
- whether the value is still active, if you know

You will receive an acknowledgement when the maintainer sees the report. There is no bounty and no fixed response window.

## What happens next

If a secret is confirmed, it will be removed from the current tree and the provider should revoke it. History rewrite is considered only when leaving the value reachable is worse than rewriting a public teaching repository. Sample datasets are not rotated, because they are not credentials.

Notebooks that train on medical or financial tables are educational. A report that a model is unfit for diagnosis or lending is accepted as a documentation issue, not as a vulnerability.
