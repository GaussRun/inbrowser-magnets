# inbrowser-magnets

A static reader page for Markdown posts addressed by sha256. The link carries the hash of the post and hints about where copies live; the page fetches the post from several static hosts at once, keeps the first response whose hash matches, and renders it. It works on a first visit, in a normal browser, with no extension, while the home host is dead, blocked or seized.

This repository is the public copy: the built reader (`index.html`, published by the integration step), the test posts under `h/<sha256>.md` and their image under `h/<sha256>.png`. GitHub serves the same bytes through four front doors: `raw.githubusercontent.com`, `cdn.jsdelivr.net`, `cdn.statically.io` and GitHub Pages at `https://gaussrun.github.io/inbrowser-magnets/`.

Source, tests and the publisher script live in a separate repository. The posts here are real text about the project and are published to Blossom servers, IPFS, Arweave, Nostr relays and Software Heritage as well; `test-content/manifest.json` in the source repository lists every copy.

## Files

| Path | What |
| --- | --- |
| `h/<sha256>.md` | a post, named by the sha256 of its exact bytes |
| `h/<sha256>.png` | an image referenced from a post as `sha256:<hex>` |
| `debug.html` | the debugger: give it the same `#v1.` link and it lists every host the reader would try, runs them all to completion and shows status, timing, bytes and sha256 per host, with an export; `https://gaussrun.github.io/inbrowser-magnets/debug.html#v1.<hex>` or `https://mulihost.0rs.org/debug.html#v1.<hex>` |
| `nostr.js`, `bluesky.js`, `arweave-graphql.js` | the reader's lazily loaded source modules (Nostr relays, Bluesky PDS blobs, Arweave GraphQL lookup), shared with the debugger |
| `404.html` | a byte copy of `index.html`, so readable-path links such as `/@gaussrun/hello-magnets#v1.<hex>` run the reader on GitHub Pages (served with status 404; the loader reads only the fragment) |
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
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets@main/h/312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0.md
- Arweave: https://arweave.net/raw/JpCbBtEL62oENawwQnAT5r-bw7jETYeP55s2KLqGacA
- reader link: https://gaussrun.github.io/inbrowser-magnets/@gaussrun/hello-magnets#v1.312453b85dbbece038586643c5cb220e8925b8a1700d121b37f4a9acdd70fcd0.5cedf17233b099062a5c68724d24b0a42fe5be22c779553debd23fc3f06a42e4.g:GaussRun/inbrowser-magnets~o:gaussrun.github.io/inbrowser-magnets~a:JpCbBtEL62oENawwQnAT5r-bw7jETYeP55s2KLqGacA

### How the reader races the hosts

- slug: `medium-post`
- size: 18468 bytes
- sha256: `61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627`
- CIDv1 raw: `bafkreidbtgiwgumnqe4m4hhi3l53butnbxtpufpzx3wpz5bskq7hq3tge4`
- home: https://gaussrun.github.io/inbrowser-magnets/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets@main/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
- Arweave: https://arweave.net/raw/Blj4iEBiBZMrcVjWC75n2j_FmMCu2n408dZSxeLRKD8
- reader link: https://gaussrun.github.io/inbrowser-magnets/@gaussrun/medium-post#v1.61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.5cedf17233b099062a5c68724d24b0a42fe5be22c779553debd23fc3f06a42e4.g:GaussRun/inbrowser-magnets~o:gaussrun.github.io/inbrowser-magnets~a:Blj4iEBiBZMrcVjWC75n2j_FmMCu2n408dZSxeLRKD8

### Field notes on every host the reader can use

- slug: `large-post`
- size: 98125 bytes
- sha256: `28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8`
- CIDv1 raw: `bafkreibi6nfymkhk67yzjxehaxgs5bwuunxerspjc5ytbbqqkeer7h2x3a`
- home: https://gaussrun.github.io/inbrowser-magnets/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets@main/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
- Arweave: https://arweave.net/raw/6ItnT2Xn4-BrG5OZv702Z-sE2rmAligSW35ifBko-p8
- reader link: https://gaussrun.github.io/inbrowser-magnets/@gaussrun/large-post#v1.28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.5cedf17233b099062a5c68724d24b0a42fe5be22c779553debd23fc3f06a42e4.g:GaussRun/inbrowser-magnets~o:gaussrun.github.io/inbrowser-magnets~a:6ItnT2Xn4-BrG5OZv702Z-sE2rmAligSW35ifBko-p8

### magnet-png (image)

- slug: `magnet-png`
- size: 203 bytes
- sha256: `95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae`
- CIDv1 raw: `bafkreievzc3mo6fdkzvowa7aijavz3natxzm2x4n7m7luxaidmie7px7vy`
- home: https://gaussrun.github.io/inbrowser-magnets/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets@main/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- Arweave: https://arweave.net/raw/nmZGxYEtK72IDl1tHVaSR3P_a2kxPsCU5nH0tBzX3yY

## Link format

```text
https://gaussrun.github.io/inbrowser-magnets/#v1.<sha256 hex>[.<author nostr pubkey>][.<hints>]
```

Hints are `~` separated `code:value` pairs: `g:user/repo` for a GitHub repository, `o:host/base` for the owner host, `a:<txid>` for an Arweave transaction, `s:host` for an extra Blossom server, `n:host` for an extra Nostr relay, `t:<template>` for any URL template with `*` in place of the hash.

## License

MIT.
