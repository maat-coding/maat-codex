# MAAT Codex — the books inside Ethereum / книги в Ethereum

A permanent, self-contained reader for the **«Egyptian Mysteries» series (Books 1–5)** and the **MAAT Manifesto**, all inscribed forever into the **Ethereum** blockchain as transaction calldata.

The full multi-book reader lives at **https://maatx.io/codex.html** — pick any book (1–5) and language (RU/EN); your browser reads it straight from the chain and verifies it.

`index.html` is a single, dependency-free HTML file (the same multi-book reader). Open it in any browser and it will:
1. read the *capstone* transaction from Ethereum via public RPCs,
2. follow it to the page-transactions,
3. reassemble the full text,
4. recompute the **Merkle root (SHA-256)** and verify it against the value recorded on-chain,
5. render the book (Russian or English).

It does **not** depend on any private server. Mirrors:
- Web: https://maatx.io/codex.html
- ENS: https://maatx.eth.limo
- Arweave (permanent, all books): https://arweave.net/UVveKYDwTF-uobcZ_ylAD90ujUqozrZ-OjhkuNljbj4

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

### Findability beacons (per book)

Each book also has a human-readable **beacon** transaction and an **ethscription** (`data:` URI) catalog entry, all sent from the inscriber address:

| Book | Beacon | Ethscription |
|------|--------|--------------|
| 1 | `0xf4bfbc14547619cbcc1ffebc1f3a452acfea7308b950507a27b539b7c3bdab85` | `0xcff50945bee09bf89b98d4f23a07256c5310acee93cebe0c840ef223ebc6238d` |
| 2 | `0xe84eee21a95b5922e2551b62c8a2a3ea61747d193bb8cd6e1982212dde97e4da` | `0xf3306939ba89ae3db1fb5db2961c6859dadc122f7444dc992aaefca045a25339` |
| 3 | `0x6f6dac35efc2400e8fa85bb0dff532da52b5adc668a62c14444a61ca69c87758` | `0xb1e6cac04ad1589e4eee6195a74e440b200a375e5d9bf0feda49c2d6c0e9de25` |
| 4 | `0x47a02bc0ca10f44adeb2fc6f863df8884971366e3482c598e1c255ee2abedd0a` | `0xf95c31c9e6c29da77950f2b500f86f31aa0502eacc1554524b90e723cd0562d7` |
| 5 | `0x1bc58747058ee84e9bf35f92514ac845305ce6bb8a0be155bc2cbcbaadec0008` | `0xd70fc74bb68e9df49792fe022ea032417c824dd505d77814a1d8a164408ff8ad` |

The complete map — every page-transaction hash, full-text SHA-256 and Merkle root for all books — is in [`MANIFEST.txt`](./MANIFEST.txt).

## How to recover the books without any website

1. Open the inscriber address on [Etherscan](https://etherscan.io/address/0x6F248C06c4bDcf018181059BD1e7Cb4eb66226e0) (or any Ethereum explorer). All page-transactions of all books are listed there.
2. Open a **capstone** transaction (see the table above or `MANIFEST.txt`). Its calldata holds a JSON document beginning with `MAAT-CODEX-1` that lists, in order, the transaction hashes of every page and the Merkle root.
3. For each page transaction, open it and choose **"View Input As → UTF-8"** — that is the raw book text.
4. Concatenate the pages in order. Recompute the Merkle root (SHA-256 of each page's bytes, folded pairwise) and compare with the capstone's `merkleRoot` to confirm authenticity.

The text is plain UTF-8 in the calldata — it can be read with nothing more than a block explorer.

## License / spirit

The text belongs to its author, Telim Maat (Дом Изменённых Маат / Pr en Ma'at Iret). This repository exists so the inscription remains discoverable and verifiable independently of any single server or domain.
