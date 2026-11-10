# Third-party sources shipped with Grit

[Grit](https://mixwithgrit.com) is built with open-source libraries. A few of
them ship in a form Grit changed. Where a library's license asks for the source
of the changed version, that source is published here, exactly as it is built
into the app.

| Directory | Based on | License |
|---|---|---|
| [`symphonia-codec-vorbis`](symphonia-codec-vorbis) | `symphonia-codec-vorbis` 0.6.1 | MPL-2.0 |
| [`symphonia-format-ogg`](symphonia-format-ogg) | `symphonia-format-ogg` 0.6.1 | MPL-2.0 |
| [`symphonia-format-riff`](symphonia-format-riff) | `symphonia-format-riff` 0.6.1 | MPL-2.0 |

Each directory is the complete crate: the files of the upstream crates.io
archive with Grit's changes applied.

- `GRIT-PATCHES.md` in each directory says what changed and why.
- Every change is marked `Grit modification` in the source.
- `LICENSE` in each directory is the license the crate stays under.

The crates belong to [Symphonia](https://github.com/pdeljanov/Symphonia) by
The Project Symphonia Developers. The unchanged archives are at
`https://crates.io/api/v1/crates/<name>/0.6.1/download`.

## Which version of Grit ships which state

| Tag | Grit versions |
|---|---|
| `symphonia-0.6.1-grit.1` | 0.1.1 to 0.1.12, and every later version until a newer tag is listed here |

In versions after 0.1.12, the notices inside the app (**Help ▸ Acknowledgements**)
link to the tag a build was made from.

## Using these copies

They replace the crates.io versions through Cargo's patch table:

```toml
[patch.crates-io]
symphonia-codec-vorbis = { git = "https://github.com/gobijan/grit-third-party-sources", tag = "symphonia-0.6.1-grit.1" }
symphonia-format-ogg = { git = "https://github.com/gobijan/grit-third-party-sources", tag = "symphonia-0.6.1-grit.1" }
symphonia-format-riff = { git = "https://github.com/gobijan/grit-third-party-sources", tag = "symphonia-0.6.1-grit.1" }
```
