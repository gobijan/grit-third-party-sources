# Grit's symphonia-codec-vorbis 0.6.1 patch

Source: the `symphonia-codec-vorbis` 0.6.1 crates.io archive (MPL-2.0, The
Project Symphonia Developers). Upstream: <https://github.com/pdeljanov/Symphonia>.

The root `[patch.crates-io]` applies this copy to every user of the crate. Only
`src/codebook.rs` and `src/lib.rs` change; each change is marked
"Grit modification".

Upstream 0.6 already refuses codebooks the reference decoder (libvorbis)
refuses: at most 32 dimensions and 2^17 entries keep `ilog(dimensions) +
ilog(entries)` within 24. It still allows 16 MiB of lookup values per book.

Local changes:

- Refuse a VQ lookup table above 2^20 values before it is allocated and filled.
- Bound what one setup header declares across all its codebooks (2^18 entries,
  whose Huffman tables can take ~30x that, and 2^22 lookup values).

A crafted setup header could otherwise make the decoder allocate and fill
gigabytes and spend minutes building tables, inside the app process.
