# Grit's symphonia-format-riff 0.6.1 patch

Source: the `symphonia-format-riff` 0.6.1 crates.io archive (MPL-2.0, The
Project Symphonia Developers). Upstream: <https://github.com/pdeljanov/Symphonia>.

The root `[patch.crates-io]` applies this copy to every user of the crate. Only
`src/wave/mod.rs` changes; the change is marked "Grit modification".

Local changes:

- Keep the WAV `LIST`/`INFO` tags the reader parses. Upstream 0.6.1 collects
  them into a local log and then returns only the leading metadata, so WAV
  titles and artists were lost on import.
