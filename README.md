# Orpheum security records

This folder is the owner's record of Orpheum's signing keys and what they have signed. It is kept
in git so every change has a date and cannot be quietly rewritten.

## What is kept here

- `ledger/`: every signed statement the tool has made, for the discovery chain and the publisher
  chain (the lists of trusted keys, the address document, the release records), and the signatures
  that go with them.
- `keys/`: the public half of every key (`*.pub` files).
- `attestations/`: the optional proof a security key gives that it made a key inside itself.
- `ceremony.json`: the notes the guided ceremony keeps so it can carry on after an interruption.
- `stubs/`: for a hardware security key, a small file that only points to the key. It is useless
  without the device and the PIN, but it stays out of git anyway (see `.gitignore`).

## Nothing in here is secret

Everything committed here is public or becomes public when published. No private key is kept here.
A private key made without a security device (the `--software` kind) lives in a separate keys
directory outside this folder, and that directory is never committed.

## Looking after it

- Keep this repository private anyway, and back it up somewhere other than the computer it is on.
- Do not edit files by hand. The `discovery-sign` tool writes them.
- Resume an interrupted ceremony by running the same `discovery-sign ceremony --folder <this folder>`
  command again.

The `.gitignore` refuses private key files by name, as a second line of defence.
