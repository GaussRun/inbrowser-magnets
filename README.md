# inbrowser-magnets

A static reader page for Markdown posts addressed by sha256. The link carries the hash of the post and hints about where copies live; the page fetches the post from several static hosts at once, keeps the first response whose hash matches, and renders it. It works on a first visit, in a normal browser, with no extension, while the home host is dead, blocked or seized.

This repository is the public copy: the built reader (`index.html`, published by the integration step), the test posts under `h/<sha256>.md` and their image under `h/<sha256>.png`. GitHub serves the same bytes through four front doors: `raw.githubusercontent.com`, `cdn.jsdelivr.net`, `cdn.statically.io` and GitHub Pages at `https://gaussrun.github.io/inbrowser-magnets/`.

Source, tests and the publisher script live in a separate repository. The posts here are real text about the project and are published to Blossom servers, IPFS, Arweave, Nostr relays and Software Heritage as well; `test-content/manifest.json` in the source repository lists every copy.

## Files

| Path | What |
| --- | --- |
| `h/<sha256>.md` | a post, named by the sha256 of its exact bytes |
| `h/<sha256>.png` | an image referenced from a post as `sha256:<hex>` |
| `.nojekyll` | tells GitHub Pages to serve files as they are |
| `.github/workflows/pages.yml` | deploys the repository root to GitHub Pages |

## Demo blog: Magnet Notes

A small blog made only of such posts: an index and 7 posts with images, every page loaded through the same hash-verified race. Open the index and click through; the footer of every page names the host that answered first.

- entry link: https://mulihost.0rs.org/@gaussrun/magnet-notes#v1.11857d7ebf52e996b4646d59bb16673187014b2a65fa02ad6ca39fcf07f5567d.5cedf17233b099062a5c68724d24b0a42fe5be22c779553debd23fc3f06a42e4.g:GaussRun/inbrowser-magnets~o:mulihost.0rs.org

- Arweave free tier limits (8276 bytes, sha256 `f8041baad05bbff69e815751e7a731312febe4c3d2e26fe51ff112e2058b1644`): null
- Blossom servers that take text (8195 bytes, sha256 `b1ab521491a8fd506c27dd599d41862604873e761eed31525d9f6a0b7e7dbb16`): null
- What we measured about browser DNS failover (12148 bytes, sha256 `cc1b13450bb6b0338d89018eba9a3a5e5d6940a1a1305d361f0d0e8ef84f9039`): null
- Why IPFS is last (8876 bytes, sha256 `a60b5f550507b99fcc58688870bb6562e45f9329da5c8fa933c08bc584e6b55f`): null
- How the link format works (10981 bytes, sha256 `5b9263cbfcc93c7222b1459a781f871e335adf7444e2ddf21c4e4dded1ee2de5`): null
- Nostr relays and the 64 KB limit (8917 bytes, sha256 `ba49920232c357ae703feee8e049a1b07cbc391487c3bb5bf7b6dfefe9362aa9`): null
- Why one https link cannot survive its host (7718 bytes, sha256 `bd1a16da7322254332a1bf541f3024267347635aa059c56533ef7ccb56cbfff2`): null

Posts link to each other by hash, so the link graph is acyclic: the index links to every post and no post contains the index hash. The reader carries the index hash in the link (`i:` hint) so each page can link back. Editing a post changes its hash and therefore the index and every later post that links to it; the build is `scripts/build-blog.mjs` in the source repository.

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
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/61999163518d8138ce1ce8dafbb0d26d0de6fa15f9beecfcf432543e786e6627.md
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
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/28f34b8628eaf7f194dc8705cd2e86d4a36e48c9e9177130861051091f9f57d8.md
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
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/95c8b6c778a3566aeb03e042415ceda09df2cd5f8dfb3eba5c081b104fbeffae.png
- Arweave: https://arweave.net/raw/nmZGxYEtK72IDl1tHVaSR3P_a2kxPsCU5nH0tBzX3yY

## Demo blog files

### Arweave free tier limits

- slug: `arweave-free`
- size: 8276 bytes
- sha256: `f8041baad05bbff69e815751e7a731312febe4c3d2e26fe51ff112e2058b1644`
- CIDv1 raw: `bafkreihyaqn2vuc3x73j5akxkht2omjrf7v6jq6s4jx6kh7rclralcywiq`
- home: https://mulihost.0rs.org/h/f8041baad05bbff69e815751e7a731312febe4c3d2e26fe51ff112e2058b1644.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/f8041baad05bbff69e815751e7a731312febe4c3d2e26fe51ff112e2058b1644.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/f8041baad05bbff69e815751e7a731312febe4c3d2e26fe51ff112e2058b1644.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/f8041baad05bbff69e815751e7a731312febe4c3d2e26fe51ff112e2058b1644.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/f8041baad05bbff69e815751e7a731312febe4c3d2e26fe51ff112e2058b1644.md

### Blossom servers that take text

- slug: `blossom-text`
- size: 8195 bytes
- sha256: `b1ab521491a8fd506c27dd599d41862604873e761eed31525d9f6a0b7e7dbb16`
- CIDv1 raw: `bafkreifrvnjbjeni7vigyj65lgoudbrgasdt45q65uyvexm7nifx47n3cy`
- home: https://mulihost.0rs.org/h/b1ab521491a8fd506c27dd599d41862604873e761eed31525d9f6a0b7e7dbb16.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/b1ab521491a8fd506c27dd599d41862604873e761eed31525d9f6a0b7e7dbb16.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/b1ab521491a8fd506c27dd599d41862604873e761eed31525d9f6a0b7e7dbb16.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/b1ab521491a8fd506c27dd599d41862604873e761eed31525d9f6a0b7e7dbb16.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/b1ab521491a8fd506c27dd599d41862604873e761eed31525d9f6a0b7e7dbb16.md

### What we measured about browser DNS failover

- slug: `dns-failover`
- size: 12148 bytes
- sha256: `cc1b13450bb6b0338d89018eba9a3a5e5d6940a1a1305d361f0d0e8ef84f9039`
- CIDv1 raw: `bafkreigmdmjukc5wwazy3cibr25juos6lvuubinbgbotmhynb2hpqt4qhe`
- home: https://mulihost.0rs.org/h/cc1b13450bb6b0338d89018eba9a3a5e5d6940a1a1305d361f0d0e8ef84f9039.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/cc1b13450bb6b0338d89018eba9a3a5e5d6940a1a1305d361f0d0e8ef84f9039.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/cc1b13450bb6b0338d89018eba9a3a5e5d6940a1a1305d361f0d0e8ef84f9039.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/cc1b13450bb6b0338d89018eba9a3a5e5d6940a1a1305d361f0d0e8ef84f9039.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/cc1b13450bb6b0338d89018eba9a3a5e5d6940a1a1305d361f0d0e8ef84f9039.md

### Magnet Notes

- slug: `index`
- size: 3700 bytes
- sha256: `58367710dcbb6891071f9133332a8624b44e8c55b351efff700666f79bb31f52`
- CIDv1 raw: `bafkreicygz3rbxf3nciqoh4rgmzsvbrewrhiyvntkhx764agm33zxmy7ki`
- home: https://mulihost.0rs.org/h/58367710dcbb6891071f9133332a8624b44e8c55b351efff700666f79bb31f52.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/58367710dcbb6891071f9133332a8624b44e8c55b351efff700666f79bb31f52.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/58367710dcbb6891071f9133332a8624b44e8c55b351efff700666f79bb31f52.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/58367710dcbb6891071f9133332a8624b44e8c55b351efff700666f79bb31f52.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/58367710dcbb6891071f9133332a8624b44e8c55b351efff700666f79bb31f52.md

### Why IPFS is last

- slug: `ipfs-last`
- size: 8876 bytes
- sha256: `a60b5f550507b99fcc58688870bb6562e45f9329da5c8fa933c08bc584e6b55f`
- CIDv1 raw: `bafkreifgbnpvkbihxgp4ywdirbylwzlc4rpzgko2lsh2sm6arpcyjzvvl4`
- home: https://mulihost.0rs.org/h/a60b5f550507b99fcc58688870bb6562e45f9329da5c8fa933c08bc584e6b55f.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/a60b5f550507b99fcc58688870bb6562e45f9329da5c8fa933c08bc584e6b55f.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/a60b5f550507b99fcc58688870bb6562e45f9329da5c8fa933c08bc584e6b55f.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/a60b5f550507b99fcc58688870bb6562e45f9329da5c8fa933c08bc584e6b55f.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/a60b5f550507b99fcc58688870bb6562e45f9329da5c8fa933c08bc584e6b55f.md

### How the link format works

- slug: `link-format`
- size: 10981 bytes
- sha256: `5b9263cbfcc93c7222b1459a781f871e335adf7444e2ddf21c4e4dded1ee2de5`
- CIDv1 raw: `bafkreic3sjr4x7gjhrzcfmkftj4b7by6gnnn65ce4lo7ehcojxpnd3rn4u`
- home: https://mulihost.0rs.org/h/5b9263cbfcc93c7222b1459a781f871e335adf7444e2ddf21c4e4dded1ee2de5.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/5b9263cbfcc93c7222b1459a781f871e335adf7444e2ddf21c4e4dded1ee2de5.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/5b9263cbfcc93c7222b1459a781f871e335adf7444e2ddf21c4e4dded1ee2de5.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/5b9263cbfcc93c7222b1459a781f871e335adf7444e2ddf21c4e4dded1ee2de5.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/5b9263cbfcc93c7222b1459a781f871e335adf7444e2ddf21c4e4dded1ee2de5.md

### Nostr relays and the 64 KB limit

- slug: `nostr-64kb`
- size: 8917 bytes
- sha256: `ba49920232c357ae703feee8e049a1b07cbc391487c3bb5bf7b6dfefe9362aa9`
- CIDv1 raw: `bafkreif2jgjaemwdk6xhap7o5dqetinqps6dsfehyo5vx55w37x6snrkve`
- home: https://mulihost.0rs.org/h/ba49920232c357ae703feee8e049a1b07cbc391487c3bb5bf7b6dfefe9362aa9.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/ba49920232c357ae703feee8e049a1b07cbc391487c3bb5bf7b6dfefe9362aa9.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/ba49920232c357ae703feee8e049a1b07cbc391487c3bb5bf7b6dfefe9362aa9.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/ba49920232c357ae703feee8e049a1b07cbc391487c3bb5bf7b6dfefe9362aa9.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/ba49920232c357ae703feee8e049a1b07cbc391487c3bb5bf7b6dfefe9362aa9.md

### Why one https link cannot survive its host

- slug: `one-link`
- size: 7718 bytes
- sha256: `bd1a16da7322254332a1bf541f3024267347635aa059c56533ef7ccb56cbfff2`
- CIDv1 raw: `bafkreif5dilnu4zcevbtfin7kqptajbgondwgwvalhcwkm7pptfvns776i`
- home: https://mulihost.0rs.org/h/bd1a16da7322254332a1bf541f3024267347635aa059c56533ef7ccb56cbfff2.md
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/bd1a16da7322254332a1bf541f3024267347635aa059c56533ef7ccb56cbfff2.md
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/bd1a16da7322254332a1bf541f3024267347635aa059c56533ef7ccb56cbfff2.md
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/bd1a16da7322254332a1bf541f3024267347635aa059c56533ef7ccb56cbfff2.md
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/bd1a16da7322254332a1bf541f3024267347635aa059c56533ef7ccb56cbfff2.md

### dns (image)

- slug: `dns`
- size: 5487 bytes
- sha256: `6a767a3179cb6c41deeccd66f4fc8758b5d42c811f16ff3c74e50f42e0491e37`
- CIDv1 raw: `bafkreidkoz5dc6olnra553gnm32pzb2ywxkczai7c37ty5hfb5boasi6g4`
- home: https://mulihost.0rs.org/h/6a767a3179cb6c41deeccd66f4fc8758b5d42c811f16ff3c74e50f42e0491e37.svg
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/6a767a3179cb6c41deeccd66f4fc8758b5d42c811f16ff3c74e50f42e0491e37.svg
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/6a767a3179cb6c41deeccd66f4fc8758b5d42c811f16ff3c74e50f42e0491e37.svg
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/6a767a3179cb6c41deeccd66f4fc8758b5d42c811f16ff3c74e50f42e0491e37.svg
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/6a767a3179cb6c41deeccd66f4fc8758b5d42c811f16ff3c74e50f42e0491e37.svg

### hosts (image)

- slug: `hosts`
- size: 5674 bytes
- sha256: `5031481b7bbce894c1926bde714a945b19a97d797e795342ff2d2654af214ae3`
- CIDv1 raw: `bafkreicqgfebw6545ckmdetl3zyuvfc3dgux26l6pfjuf7znezkk6ikk4m`
- home: https://mulihost.0rs.org/h/5031481b7bbce894c1926bde714a945b19a97d797e795342ff2d2654af214ae3.svg
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/5031481b7bbce894c1926bde714a945b19a97d797e795342ff2d2654af214ae3.svg
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/5031481b7bbce894c1926bde714a945b19a97d797e795342ff2d2654af214ae3.svg
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/5031481b7bbce894c1926bde714a945b19a97d797e795342ff2d2654af214ae3.svg
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/5031481b7bbce894c1926bde714a945b19a97d797e795342ff2d2654af214ae3.svg

### race (image)

- slug: `race`
- size: 5148 bytes
- sha256: `8dafe1b323326059495fc98751b1ef64e2ce1deec57703c35b72f901dc4e49ef`
- CIDv1 raw: `bafkreienv7q3gizsmbmusx6jq5i3d33e4lhb33wfo4b4gw3s7ea5ytsj54`
- home: https://mulihost.0rs.org/h/8dafe1b323326059495fc98751b1ef64e2ce1deec57703c35b72f901dc4e49ef.svg
- GitHub Pages: https://gaussrun.github.io/inbrowser-magnets/h/8dafe1b323326059495fc98751b1ef64e2ce1deec57703c35b72f901dc4e49ef.svg
- GitHub raw: https://raw.githubusercontent.com/GaussRun/inbrowser-magnets/main/h/8dafe1b323326059495fc98751b1ef64e2ce1deec57703c35b72f901dc4e49ef.svg
- jsDelivr: https://cdn.jsdelivr.net/gh/GaussRun/inbrowser-magnets@main/h/8dafe1b323326059495fc98751b1ef64e2ce1deec57703c35b72f901dc4e49ef.svg
- Statically: https://cdn.statically.io/gh/GaussRun/inbrowser-magnets/main/h/8dafe1b323326059495fc98751b1ef64e2ce1deec57703c35b72f901dc4e49ef.svg

## Link format

```text
https://gaussrun.github.io/inbrowser-magnets/#v1.<sha256 hex>[.<author nostr pubkey>][.<hints>]
```

Hints are `~` separated `code:value` pairs: `g:user/repo` for a GitHub repository, `o:host/base` for the owner host, `a:<txid>` for an Arweave transaction, `s:host` for an extra Blossom server, `n:host` for an extra Nostr relay, `t:<template>` for any URL template with `*` in place of the hash.

## License

MIT.
