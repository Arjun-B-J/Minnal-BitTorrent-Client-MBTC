# Minnal-BitTorrent-Client-MBTC

A BitTorrent client written in Python. *Minnal* (மின்னல்) is Tamil for "lightning."

## Status

Early work-in-progress. The repository currently contains exploratory code for the asynchronous networking layer that the client will be built on top of. The core BitTorrent protocol (bencoding, tracker communication, peer wire protocol, piece selection, etc.) has not yet been implemented.

## Tech stack

- **Language:** Python 3
- **Concurrency:** `asyncio` — the standard library's coroutine-based async I/O framework, used to manage many concurrent peer connections without threads.

No third-party dependencies so far.

## Repository layout

```
.
├── test.py       # asyncio sandbox: opens concurrent TCP connections as a warm-up for peer I/O
├── .gitignore
└── README.md
```

## Running

The current `test.py` is a small experiment that opens two concurrent TCP connections (to `8.8.8.8:53` and `8.8.4.4:53`) using `asyncio.open_connection`, holds them open for a random short interval, and closes them.

Requires Python 3.7+ (for `asyncio.get_event_loop` / `asyncio.ensure_future` semantics used here).

```bash
python test.py
```

## Roadmap

The intended scope of a minimal BitTorrent client includes:

- `.torrent` file parsing (bencoding decoder)
- Tracker protocol (HTTP/UDP announce)
- Peer wire protocol handshake and message framing
- Piece selection strategy and download/verify loop (SHA-1 piece hashes)
- Local file assembly

These pieces are not implemented yet — contributions and progress will be tracked in this repo.
