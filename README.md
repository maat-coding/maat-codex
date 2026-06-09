# MAAT Codex — the books inside Ethereum / книги в Ethereum

A permanent, self-contained reader for the **«Egyptian Mysteries» series (Books 1–5)** and the **MAAT Manifesto**, all inscribed forever into the **Ethereum** blockchain as transaction calldata.

The full multi-book reader lives at **https://maatx.io/codex.html** — pick any book (1–5) and language (RU/EN); your browser reads it straight from the chain and verifies it.

`index.html` is a single, dependency-free HTML file. Open it in any browser and it will:
1. read the *capstone* transaction from Ethereum via public RPCs,
2. follow it to the page-transactions,
3. reassemble the full text,
4. recompute the **Merkle root (SHA-256)** and verify it against the value recorded on-chain,
5. render the book (Russian or English).

It does **not** depend on any private server. Mirrors:
- Web: https://maatx.io/codex.html
- Arweave (permanent): https://arweave.net/QYPJ6Ns9Q8vlSbMwuamhZaE1Hod4fkZaTVdh7e_SrqA

## On-chain coordinates

Every page-transaction was sent from the **inscriber address**:
`0x6F248C06c4bDcf018181059BD1e7Cb4eb66226e0`

**MAAT token (ERC-20):** `0x1ae560e95d0c8ec6B338DeAD8f44A3BAeE48d4e9`

### Capstones (one per book + language)

| Book | RU capstone | EN capstone |
|------|-------------|-------------|
| 1 — Книга первая | `0xefde4918e5149898261062b0a60398ff462ca92e341f3fd7c7e11d21418bf21c` | `0x8c11bca2c911eb9c4c0c9b71a11ed3c312b1bb8e432a6b9ac13f128a75279ecd` |
| 2 — Ключи Осириса | `0x5dfc340e7dd2f7b356925041eeb11d353dcb19a9dbcf6249c9766e221519d970` | `0x4b26a8ebc2e09eee199b5335e78b402f8fe49d12f530c4fa345f026eaea5da7d` |
| 3 — Ключи Анубиса | `0x7de6c08aec8cead78dc0c4cd228dce2401cedeac5fed2e6434a14cc040415468` | `0xd676dcf917ee0fed2de4c5dc432c4c8f8dc955dbe949d79faaa7b096d07693ca` |
| 4 — Семь Ключей | `0x3351ac5e4b52b0038e2d0b817835e6cd3131806b11c8f3b237135a8b122fd67b` | `0x9637c5add2af51f5fcacaf4f94cd8db40d5e7e13d251b538049bf45dff3b4297` |
| 5 — Архитектура Хаоса | `0xeefc221829506c54feba06848bd331b8d5bb5dcbad4d419159784e66791c1872` | `0xb9096716d036dcbc36c1225593560e79a90408917f0417abdbb616dfa2b4f33a` |

The complete map — every page-transaction hash, full-text SHA-256 and Merkle root for all books — is in [`MANIFEST.txt`](./MANIFEST.txt).

## How to recover the books without any website

1. Open the inscriber address on [Etherscan](https://etherscan.io/address/0x6F248C06c4bDcf018181059BD1e7Cb4eb66226e0) (or any Ethereum explorer). All page-transactions are listed there.
2. Open a **capstone** transaction (see the table above or `MANIFEST.txt`). Its calldata holds a JSON document beginning with `MAAT-CODEX-1` that lists, in order, the transaction hashes of every page and the Merkle root.
3. For each page transaction, open it and choose **"View Input As → UTF-8"** — that is the raw book text.
4. Concatenate the pages in order. Recompute the Merkle root (SHA-256 of each page's bytes, folded pairwise) and compare with the capstone's `merkleRoot` to confirm authenticity.

The text is plain UTF-8 in the calldata — it can be read with nothing more than a block explorer.

## License / spirit

The text belongs to its author, Telim Maat (Дом Изменённых Маат / Pr en Ma'at Iret). This repository exists so the inscription remains discoverable and verifiable independently of any single server or domain.
