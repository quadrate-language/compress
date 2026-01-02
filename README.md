# compress

Compression and decompression using gzip/zlib for [Quadrate](https://git.sr.ht/~klahr/quadrate).

## Installation

```bash
quadpm install https://github.com/quadrate-language/compress
```

**Note**: This module requires native compilation. The C source files in `src/` must be compiled and linked. Requires zlib.

## Usage

```quadrate
use compress

fn main() {
    // Compress with gzip
    "Hello, World!" compress::gzip! -> compressed

    // Decompress
    compressed compress::gunzip! -> original
    original print nl  // "Hello, World!"

    // Compress with specific level
    "data" compress::LevelBest compress::gzip_level! -> best_compressed

    // Raw deflate (no gzip header)
    "data" compress::deflate! -> deflated
    deflated compress::inflate! -> inflated
}
```

## Compression Levels

| Constant | Value | Description |
|----------|-------|-------------|
| `LevelFast` | 1 | Fastest compression (least compression) |
| `LevelDefault` | 6 | Default balance of speed and size |
| `LevelBest` | 9 | Best compression (slowest) |

## Error Codes

| Constant | Value | Description |
|----------|-------|-------------|
| `ErrAlloc` | 2 | Memory allocation failed |
| `ErrInvalidArg` | 3 | Invalid argument |
| `ErrCompress` | 4 | Compression failed |
| `ErrDecompress` | 5 | Decompression failed |

## Functions

| Function | Description |
|----------|-------------|
| `gzip!` | Compress with gzip format (default level) |
| `gzip_level!` | Compress with gzip format at specified level |
| `gunzip!` | Decompress gzip data |
| `deflate!` | Compress with raw deflate (no header) |
| `inflate!` | Decompress raw deflate data |

## License

Apache-2.0 - See [LICENSE](LICENSE) for details.

## Contributing

Contributions welcome! Please open an issue or submit a pull request on [GitHub](https://github.com/quadrate-language/compress).
