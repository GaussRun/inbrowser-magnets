# inbrowser-magnets

A static reader page for Markdown posts addressed by sha256. The link carries the hash of the post and hints about where copies live; the page fetches the post from several static hosts at once, keeps the first response whose hash matches, and renders it. It works on a first visit, in a normal browser, with no extension, while the home host is dead, blocked or seized.

This repository is the public copy: the built reader (`index.html`, published by the integration step), the test posts under `h/<sha256>.md` and their image under `h/<sha256>.png`. GitHub serves the same bytes through four front doors: `raw.githubusercontent.com`, `cdn.jsdelivr.net`, `cdn.statically.io` and GitHub Pages at `https://gaussrun.github.io/inbrowser-magnets/`.

Source, tests and the publisher script live in a separate repository. The posts here are real text about the project and are published to Blossom servers, IPFS, Arweave, Nostr relays and Software Heritage as well; `test-content/manifest.json` in the source repository lists every copy.

## Files

| Path | What |
| --- | --- |
| `index.html` | the reader, one self-contained file (the loader) |
| `nostr.js`, `bluesky.js`, `arweave-graphql.js` | optional source modules the reader imports on demand |
| `h/<sha256>.md` | a post, named by the sha256 of its exact bytes |
| `h/<sha256>` | an image referenced from a post as `sha256:<hex>`; the reader asks for this extension-less name |
| `h/<sha256>.png` | the same image with its extension, for people |
| `.nojekyll` | tells GitHub Pages to serve files as they are |
| `.github/workflows/pages.yml` | deploys the repository root to GitHub Pages |

## Test posts

### Hello magnets

- slug: `hello-magnets`
- size: 995 bytes
- sha256: `312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0`
- CIDv1 raw: `bafkreibrerj3qxn35tqdqwdgipc4wiqores3rilqbujbwn7uvgwn24h42a`
- home: https://gaussrun.github.io/inbrowser-magnets/h/312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0.md

### How the reader races the hosts

- slug: `medium-post`
- size: 18468 bytes
- sha256: `61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627`
- CIDv1 raw: `bafkreidbtgiwgumnqe4m4hhi3l53butnbxtpufpzx3wpz5bskq7hq3tge4`
- home: https://gaussrun.github.io/inbrowser-magnets/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md

### Field notes on every host the reader can use

- slug: `large-post`
- size: 98125 bytes
- sha256: `28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8`
- CIDv1 raw: `bafkreibi6nfymkhk67yzjxehaxgs5bwuunxerspjc5ytbbqqkeer7h2x3a`
- home: https://gaussrun.github.io/inbrowser-magnets/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md

### magnet-png (image)

- slug: `magnet-png`
- size: 203 bytes
- sha256: `95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae`
- CIDv1 raw: `bafkreievzc3mo6fdkzvowa7aijavz3natxzm2x4n7m7luxaidmie7px7vy`
- home: https://gaussrun.github.io/inbrowser-magnets/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png

## Link format

```text
https://gaussrun.github.io/inbrowser-magnets/#v1.<sha256 hex>[.<author nostr pubkey>][.<hints>]
```

Hints are `~` separated `code:value` pairs: `g:user/repo` for a GitHub repository, `o:host/base` for the owner host, `a:<txid>` for an Arweave transaction, `s:host` for an extra Blossom server, `n:host` for an extra Nostr relay, `t:<template>` for any URL template with `*` in place of the hash, `u:<url>` for one literal URL, `ns:<npub>` for an nsite under that key, `b:<did>[/<blobcid>]` for a blob on an AT Protocol PDS. Without any hint the reader still asks the built-in Blossom servers, Software Heritage, Nostr relays and the Arweave index by hash alone.

Open the test posts through this copy of the reader:

- https://gaussrun.github.io/inbrowser-magnets/#v1.312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0.g:GaussRun/inbrowser-magnets~o:mulihost.0rs.org
- https://gaussrun.github.io/inbrowser-magnets/#v1.61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.g:GaussRun/inbrowser-magnets~o:mulihost.0rs.org
- https://gaussrun.github.io/inbrowser-magnets/#v1.28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.g:GaussRun/inbrowser-magnets~o:mulihost.0rs.org

The same reader is served at https://mulihost.0rs.org/ (home host), on the nsite gateways under `npub1c89g65emcv4ggxmqjcawxx0fwv943kn9rz307n9vvcnwe2xtu6lq0ma47a` and on Arweave; the private source repository's report lists every copy.

## License

MIT.
