<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Use-Tessera/.github/main/assets/logo-dark.svg">
    <img src="https://raw.githubusercontent.com/Use-Tessera/.github/main/assets/logo.svg" alt="Tessera" height="64">
  </picture>
</p>

<p align="center"><b>Threshold signing for Stellar. Any t of n parties sign as one ordinary account.</b></p>

Tessera splits a Stellar account's key with FROST (RFC 9591). Any `t` of `n`
signers produce one standard Ed25519 signature: no contract, no multisig
overhead, and a signer set nobody can see on chain. Every signer decodes what
it signs and enforces its own policy, so a compromised coordinator or AI agent
can't move funds past the rules.

| Repository | Language | What it does |
|---|---|---|
| [tessera](https://github.com/Use-Tessera/tessera) | Rust | Signing core, policy engine, `tessera-signer` daemon, `tessera` CLI |
| [tessera-coordinator](https://github.com/Use-Tessera/tessera-coordinator) | Go | Runs signing sessions, verifies signatures, submits, keeps a hash-chained audit log |

Proven on testnet: a 2-of-3 group, with one signer offline, paid on chain with a
single signature, and both remaining signers refused a payment over their limit.

We take part in the [Stellar Wave](https://www.drips.network/wave/stellar)
program. Look for issues labeled by complexity in each repository.
