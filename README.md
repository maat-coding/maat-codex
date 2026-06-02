# MAAT Codex — the book inside Ethereum / книга в Ethereum

This is a permanent, self-contained reader for the book **«Architecture of Chaos. Architecture of Maat» (Egyptian Mysteries 5)** and the **MAAT Manifesto**, both inscribed forever into the **Ethereum** blockchain as transaction calldata.

`index.html` is a single, dependency-free HTML file. Open it in any browser and it will:
1. read the *capstone* transaction from Ethereum via public RPCs,
2. follow it to the page-transactions,
3. reassemble the full text,
4. recompute the **Merkle root (SHA-256)** and verify it against the value recorded on-chain,
5. render the book (Russian or English).

It does **not** depend on any private server. Mirrors:
- Web: https://maatx.io/codex.html
- Arweave (permanent): https://arweave.net/QYPJ6Ns9Q8vlSbMwuamhZaE1Hod4fkZaTVdh7e_SrqA

## On-chain coordinates (everything you need to recover the book by hand)

- **Inscriber address** (every page-transaction was sent from it):
  `0x6F248C06c4bDcf018181059BD1e7Cb4eb66226e0`
- **Capstone — Russian book:**
  `0xeefc221829506c54feba06848bd331b8d5bb5dcbad4d419159784e66791c1872`
- **Capstone — English book:**
  `0xb9096716d036dcbc36c1225593560e79a90408917f0417abdbb616dfa2b4f33a`
- **MAAT token (ERC-20):** `0x1ae560e95d0c8ec6B338DeAD8f44A3BAeE48d4e9`

## How to recover the book without any website

1. Open the inscriber address on [Etherscan](https://etherscan.io/address/0x6F248C06c4bDcf018181059BD1e7Cb4eb66226e0) (or any Ethereum explorer). All page-transactions are listed there.
2. Open a **capstone** transaction. Its calldata holds a JSON document beginning with `MAAT-CODEX-1` that lists, in order, the transaction hashes of every page and the Merkle root.
3. For each page transaction, open it and choose **"View Input As → UTF-8"** — that is the raw book text.
4. Concatenate the pages in order. Recompute the Merkle root (SHA-256 of each page's bytes, folded pairwise) and compare with the capstone's `merkleRoot` to confirm authenticity.

The text is plain UTF-8 in the calldata — it can be read with nothing more than a block explorer.

## License / spirit

The text belongs to its author, Telim Maat (Дом Изменённых Маат / Pr en Ma'at Iret). This repository exists so the inscription remains discoverable and verifiable independently of any single server or domain.
