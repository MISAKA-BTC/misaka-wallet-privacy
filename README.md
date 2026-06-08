# MISAKA Wallet — Privacy Policy

_Last updated: 2026-06-08_

Privacy policy for **MISAKA Wallet**, the self-custody, post-quantum (ML-DSA-87) Chrome extension
for the MISAKA (kaspa-pq) network.

**Published page:** https://misaka-btc.github.io/misaka-wallet-privacy/

---

MISAKA Wallet ("the extension") is a **self-custody, client-side** browser extension for the MISAKA
(kaspa-pq) post-quantum network. It is designed to handle as little data as possible.

> **In short:** We collect **nothing** — no developer server, no account, no analytics, no
> telemetry, no tracking. Your keys are encrypted and **never leave your device**. The only network
> traffic is the blockchain requests your wallet makes to show balances and send transactions.

## 1. Data we collect
**None.** The developer operates **no backend server** for this extension and receives **no**
personal data, analytics, telemetry, or usage statistics from it.

## 2. Data stored on your device (never transmitted)
- **Recovery phrase / private key** — encrypted with **AES-256-GCM** under a key derived from your
  password via **PBKDF2-HMAC-SHA-512 (600,000 iterations)**, stored only in the browser's
  extension-local storage. It is **never** stored in plaintext and **never** transmitted. A wrong
  password fails authentication — there is no decryption oracle.
- **Settings** — selected network, auto-lock timeout, and an optional custom node URL.

The decrypted key exists only in volatile memory while the wallet is unlocked, and is wiped on
manual lock, idle auto-lock, or browser close.

## 3. Network connections
To show balances and broadcast transactions, the extension connects **directly from your browser**
to a MISAKA node and block explorer (by default `misakascan.com`, or a custom node URL you set):
- **WebSocket RPC** (`wss://misakascan.com/kaspa`) — read your address's balance/UTXOs and submit
  the transactions you sign.
- **Explorer REST API** (`https://misakascan.com/addresses/…`) — fetch your address's transaction
  history for the Activity view.
- **Local node** (`ws://127.0.0.1`, `ws://localhost`) — used only if you choose to run your own node.

These requests contain only the public blockchain data needed: your **public address** (to query it)
and the **signed transactions** you choose to send. Your private key is **never** sent. As with any
blockchain node, the node/explorer operator can observe the public addresses and transactions queried
through it; set your own node URL in Settings if you prefer.

## 4. Permissions
- `storage` — save your encrypted vault and settings locally.
- `alarms` — enforce the idle auto-lock timer.
- host access to `*.misakascan.com`, `127.0.0.1`, and `localhost` — connect to the MISAKA
  node/explorer to read balances and submit transactions.

## 5. Remote code
The extension loads **no remote code**. All JavaScript and the WebAssembly signing core are bundled
in the package; the Content Security Policy forbids remote scripts.

## 6. Data sharing & sale
We do **not** sell or transfer your data to third parties. We do **not** use or transfer your data
for any purpose unrelated to the wallet's single purpose, and **never** for determining
creditworthiness or for lending. (We hold no such data to begin with.)

## 7. Children
The extension is a financial tool and is not directed to children under 13.

## 8. Changes to this policy
We may update this policy from time to time. Changes are posted here with a new "Last updated" date.

## 9. Contact
Questions or requests: open an issue at https://github.com/MISAKA-BTC/misakas
