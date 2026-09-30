# Ghost in the GPU · Forensics

**Core idea:** the VRAM dump contained a tensor, not a conventional image file. The metadata specified how to turn its raw floats back into pixels.

## Reconstructing the view

Metadata near offset `0x100000` described a `1×3×512×512` tensor of `float16` values with NCHW layout. The buffer began at `0x00900000`. Reading `3×512×512×2` bytes from that offset, reshaping to three channel planes, and transposing from `C,H,W` to `H,W,C` produced the pixel grid.

Values were normalized approximately to `[-1,1]`; applying `((value + 1) / 2) × 255`, clipping, and converting to `uint8` yielded a readable RGB image. Treating the data as interleaved HWC bytes or as ordinary unsigned integers hid the writing.

## Evidence and limits

The private work directory retains the reconstructed PNG. I inspected it during publication: the flag is visibly spelled out in the image. The old solver also printed the flag as a constant, but the **image**, not that hard-coded line, is the evidence here.

**Flag:** `zdk{m3MoRy_Le4k_fouNd}`

**Lesson:** a recovered rendering should independently support any string copied into a solver.
