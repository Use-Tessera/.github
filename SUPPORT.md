# Getting help

- **Would my signers sign this?** `tessera check --policy policy.toml --account G… <envelope>`
  answers locally, with the reasons for any refusal. Add `--latest-ledger N`
  to judge a Soroban authorization entry instead.
- **Setting up a group:** the [tessera README](https://github.com/Use-Tessera/tessera#readme)
  walks through distributed key generation, signer configuration and share
  refresh; [`examples/policy.toml`](https://github.com/Use-Tessera/tessera/blob/main/examples/policy.toml)
  documents every policy setting.
- **Running sessions or submitting:** the
  [coordinator README](https://github.com/Use-Tessera/tessera-coordinator#readme)
  and its [OpenAPI description](https://github.com/Use-Tessera/tessera-coordinator/blob/main/api/openapi.yaml).
- **What each party can and cannot do:** the
  [security model](https://github.com/Use-Tessera/tessera/blob/main/docs/security-model.md).
- **Bugs:** open one in the repository concerned, with the command, the
  (redacted) policy and the output. Never paste a share file or passphrase.
- **Anything that leaks key material or gets a signature past a policy** is a
  security issue: report it privately as described in [SECURITY.md](SECURITY.md).
