<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Use-Tessera/.github/main/assets/logo-dark.svg">
    <img src="https://raw.githubusercontent.com/Use-Tessera/.github/main/assets/logo.svg" alt="Tessera" height="64">
  </picture>
</p>

<p align="center"><b>Threshold signing for Stellar. Any t of n parties sign as one ordinary account.</b></p>

<p align="center"><a href="https://use-tessera.github.io/tessera/"><b>Check a transaction against a signer policy →</b></a> · <a href="https://github.com/Use-Tessera/tessera-coordinator/tree/main/examples/compose">Run a 2-of-3 group with Docker</a></p>

Tessera splits a Stellar account's key with FROST (RFC 9591). Any `t` of `n`
signers produce one standard Ed25519 signature: no contract, no multisig
overhead, and a signer set nobody can see on chain. Every signer decodes what
it signs and enforces its own policy, so a compromised coordinator or AI agent
cannot move funds past the rules.

| Repository | Language | What it does |
|---|---|---|
| [tessera](https://github.com/Use-Tessera/tessera) | Rust | Signing core, distributed key generation and share refresh, policy engine, `tessera-signer`, `tessera` CLI |
| [tessera-coordinator](https://github.com/Use-Tessera/tessera-coordinator) | Go | Runs signing sessions, verifies every signature itself, submits, keeps a hash-chained audit log |

**What it signs:** transactions, and Soroban authorization entries, so a group
can authorize a contract call that someone else submits (an x402 payment, a
relayer). Policies cap amounts per asset and per SEP-41 token, per transaction
and per day, and bound how long any signature stays valid.

**Keys without a dealer:** `tessera dkg` generates the group key so it never
exists on one machine, over a relay that cannot read or alter what passes
through it; `tessera dkg start --refresh` re-randomises shares on a schedule
without changing the account.

**Proven on testnet:** a 2-of-3 group, with one signer offline, paid on chain
with a single signature, and both remaining signers refused a payment over
their limit.

**Contributing:** we take part in the
[Stellar Wave](https://www.drips.network/wave/stellar) program; issues are
labeled by complexity. Read [CONTRIBUTING](https://github.com/Use-Tessera/.github/blob/main/CONTRIBUTING.md)
first, and report security issues privately as described in
[SECURITY](https://github.com/Use-Tessera/.github/blob/main/SECURITY.md).
