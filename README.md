# Telegraph Sentinel scorer binaries

Compiled scoring modules for the [Telegraph protocol](https://telegraphprotocol.com),
intent `FRAUD_DETECTION`. Each `.wasm` here is registered on-chain and fetched by a
Telegraph node from a commit-pinned raw URL, so these files are kept stable and are
never rewritten.

Built for Telegraph Hackathon Season I, Track 2 (Script Authors).
Source is maintained separately; this repository hosts only the compiled artefacts.

Each module is a freestanding `wasm32-unknown-unknown` build exporting `alloc`,
`dealloc` and `rank_answer`. A WASI build would carry imports a node cannot bind.

## Verify a binary

The keccak256 of any file here matches the hash stored in its on-chain registration:

```bash
node -e "const{readFileSync}=require('fs');const{ethers}=require('ethers');console.log(ethers.keccak256(readFileSync(process.argv[1])))" <file>.wasm
```

## Licence

MIT.
