# DisAssemble

A comprehensive collection of NES game disassemblies and reverse engineering tools, focusing on complete, buildable assembly source code and supporting utilities.

## Overview

This repository contains fully disassembled and reverse-engineered NES games with complete assembly source code that can be reassembled into working ROM files. The primary focus is on providing accurate, well-documented disassemblies along with the tools and methodologies needed for NES reverse engineering.

## Games Included

### Battletoads (Complete)
- **Full assembly source code** (`Battletoads (U) [!].asm`)
- **Buildable ROM** with batch scripts for assembly
- **Complete asset extraction** including graphics, music, and level data
- **IDA Pro database** with symbols and analysis
- **Memory mapping documentation** for game objects and variables

### Battletoads & Double Dragon
- **IDA Pro database** with initial analysis
- **Foundation for future disassembly work**

## Repository Structure

```
DisAssemble/
├── Battletoads/              # Complete Battletoads disassembly
│   ├── Battletoads (U) [!].asm    # Main assembly source file
│   ├── BuildROM.bat              # ROM building script
│   ├── BuildROMWithSymbols.bat   # ROM building with debug symbols
│   ├── asm6.exe                  # ASM6 assembler
│   ├── data/                     # Game data files (levels, animations)
│   ├── gfx/                      # Graphics assets (.chr, .4 formats)
│   └── music/                    # Music and audio data
├── Battletoads&DoubleDragon/     # Second game database
├── Utils/                        # Reverse engineering tools
│   ├── loaders/                  # IDA Pro loader files for NES
│   ├── scripts/                  # IDC scripts for automation
│   └── bt_unpack_4.exe          # Asset unpacking utility
├── RandomStuff/                  # Additional resources
│   ├── ram_map.txt              # Memory layout documentation
│   └── *.idb                   # Additional IDA databases
└── TraceLogs/                    # FCEUX emulator trace logs
```

## Features

### Complete Disassembly
- **Buildable source code** that assembles to identical ROM files
- **Comprehensive symbol naming** for functions, variables, and constants
- **Detailed comments** explaining game mechanics and algorithms
- **Organized code structure** with clear module separation

### Asset Management
- **Graphics extraction** in multiple formats (.chr, .4, .bin)
- **Level data** including maps, tile sets, and attributes
- **Music and sound data** with proper organization
- **Animation sequences** and sprite definitions

### Development Tools
- **IDA Pro integration** with custom loaders and scripts
- **ROM building automation** with batch scripts
- **Asset unpacking utilities** for graphics and data extraction
- **Memory mapping tools** for understanding game structure

### Documentation
- **RAM memory maps** documenting object structures and variables
- **Trace logs** for debugging and analysis
- **Code organization** following NES development conventions

## Requirements

### For Building ROMs
- **ASM6 Assembler** (included in repository)
- **Windows environment** (for batch scripts) or compatible shell
- **Original ROM file** (not included - must be legally obtained)

### For Reverse Engineering
- **IDA Pro** (for working with .idb files and scripts)
- **FCEUX Emulator** (for trace logs and debugging)
- **Hex editor** (for binary analysis)
- **Basic 6502 assembly knowledge**

## Quick Start

### Building the Battletoads ROM

1. **Navigate to the Battletoads directory**:
   ```bash
   cd Battletoads/
   ```

2. **Run the build script**:
   ```batch
   BuildROM.bat
   ```
   
   Or for debug symbols:
   ```batch
   BuildROMWithSymbols.bat
   ```

3. **Output**: `Battletoads (U) [!].nes` - A playable ROM file

### Working with IDA Pro

1. **Load the IDA database**:
   - Open `Battletoads (U) [!].idb` in IDA Pro
   - Use the included loader files in `Utils/loaders/` for proper NES format support

2. **Apply automation scripts**:
   - Run IDC scripts from `Utils/scripts/` for enhanced analysis
   - Use `NesMap.idc` for FCEUX trace log integration

### Understanding Game Structure

- **Consult `RandomStuff/ram_map.txt`** for memory layout
- **Review assembly source** for game logic and mechanics
- **Examine trace logs** in `TraceLogs/` for runtime behavior

## Tools and Utilities

### Assemblers
- **asm6.exe**: Standard NES assembler for building ROMs
- **asm6_sonder.exe**: Modified version with additional debug features

### Graphics Tools
- **bt_unpack_4.exe**: Unpacks compressed graphics files (.4 format)
- **Various .chr files**: Raw graphics data for sprites and backgrounds

### IDA Pro Integration
- **ines.ldw / ines_mmc3_b.ldw**: NES ROM loaders
- **HardwiredBank.idc**: Script for analyzing fixed bank code
- **NesMap.idc**: Integration with FCEUX trace logs
- **Offsets.idc**: Memory offset calculation utilities

### Analysis Tools
- **FCEUX trace logs**: Runtime execution traces for debugging
- **CDL files**: Code/data logging for coverage analysis
- **Memory maps**: Documentation of RAM usage and object structures

## File Formats

### Graphics Formats
- **.chr**: Raw CHR-ROM graphics data (8x8 pixel tiles)
- **.4**: Compressed graphics format (custom compression)
- **.bin**: Binary data files (maps, attributes, etc.)

### Assembly Files
- **.asm**: Main assembly source files
- **.lst**: Assembly listing with addresses
- **.map**: Symbol mapping files

### Analysis Files
- **.idb**: IDA Pro database files
- **.nl**: Namelist files for different memory banks
- **.cdl**: FCEUX code/data logging files

## Contributing

This repository welcomes contributions in several areas:

### Code Improvements
- **Enhanced commenting** of assembly source
- **Bug fixes** in disassembly accuracy
- **Code organization** improvements

### New Games
- **Additional NES game disassemblies** following established conventions
- **Supporting tools** for new game formats
- **Documentation** for reverse engineering methodologies

### Tool Development
- **Improved utilities** for asset extraction
- **Enhanced IDA scripts** for automation
- **Cross-platform tools** for non-Windows users

See `README.dev` for detailed development guidelines and workflows.

## Legal Notice

This repository contains only reverse-engineered assembly source code and analysis tools. **No copyrighted ROM files or game assets are included**. Users must legally obtain original game ROMs to use with this disassembly code.

The disassembly work is provided for educational and preservation purposes, following fair use principles for reverse engineering.

## License

This project is provided as-is for educational and research purposes. Please respect applicable copyright laws and fair use guidelines when using this material.