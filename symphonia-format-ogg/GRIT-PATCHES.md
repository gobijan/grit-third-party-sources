# Grit's symphonia-format-ogg 0.6.1 patch

Source: the `symphonia-format-ogg` 0.6.1 crates.io archive (MPL-2.0, The
Project Symphonia Developers). Upstream: <https://github.com/pdeljanov/Symphonia>.

The root `[patch.crates-io]` applies this copy to every user of the crate. Only
`src/mappings/vorbis.rs` and `src/demuxer.rs` change; each change is marked
"Grit modification".

Local changes:

- Ignore Vorbis setup header packets after the first. Upstream appends every
  one to the codec's extra data, copying all earlier ones each time, so a
  stream of repeated setup packets costs quadratic work inside a single
  packet read that import cancellation cannot interrupt.
- Refuse a physical stream with more than 16 logical streams. Finding each
  physical stream's end scans one maximum page per logical stream from the
  file's end, again at every chain boundary.
