<div align="center">

<img src="snap/gui/capa.png" alt="capa logo" width="128" />

# capa

**Identify capabilities in executable files**

[![capa](https://snapcraft.io/capa/badge.svg)](https://snapcraft.io/capa)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [capa](https://github.com/mandiant/capa), the FLARE team's tool that detects what PE, ELF and .NET programs and shellcode can do, using a bundled rule set and FLIRT signatures.

</div>

---

## Getting Started

<a href="https://snapcraft.io/capa"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install capa
capa suspicious.exe
```

Add `-v` or `-vv` for the addresses and features behind each match, `--json` for a machine-readable report, and `-f sc32` or `-f sc64` for raw shellcode. Run `capa --help` for every option.

The snap also includes these upstream helper scripts:

| Command | Purpose |
| --- | --- |
| `capa.show-features` | Print the features capa extracts from a file |
| `capa.capafmt` | Format a capa rule file |
| `capa.capa2yara` | Convert capa rules to YARA rules |

## Configure

The standard rules and signatures matching this release are included. To use your own rules or signatures, pass their location:

```bash
capa -r ~/capa-rules suspicious.exe
capa -s ~/sigs suspicious.exe
```

capa keeps its rule cache in `~/snap/capa/common/.cache`.

To analyze files on USB drives and other removable media (`/media`, `/mnt`), connect:

```bash
sudo snap connect capa:removable-media
```

## Limitations

- The IDA (`-b ida`), Binary Ninja (`-b binja`) and Ghidra (`-b ghidra`) backends need those programs on the host and are unavailable. Export a BinExport2 file from them and analyze it instead.
- Only files in your home directory and, once connected, on removable media can be analyzed. Hidden files directly under your home directory and system directories such as `/tmp` are inaccessible.
- The IDA, Binary Ninja and Ghidra plugins, the capa Explorer web interface and the rule linter are not included.

## Build

```bash
git clone https://github.com/sidalit/capa-snap.git
cd capa-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/capa-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/mandiant/capa/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/capa-snap/blob/main/LICENSE).
