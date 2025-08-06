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

## Battletoads Game Genie Codes

As part of the comprehensive reverse engineering documentation, this repository includes a reference for Battletoads Game Genie codes. These codes provide valuable insights into game mechanics, memory addresses, and behavioral modifications that complement the disassembly analysis.

**Reference Source**: [Battletoads Analysis Video](https://www.youtube.com/watch?v=4AwA90VxgWU)

### Code Reference Image

![Battletoads Game Genie Codes](images/battletoads-game-genie-codes.png)

*Note: Image placeholder - the actual reference image showing all Game Genie codes organized by category should be placed in the `images/` directory.*

### Code Categories and Functions

#### Partial Bypass for Tunnel
These codes modify the notorious Turbo Tunnel level mechanics:

- **ALEYAUSS** - Relocate Second Speed Limit
  - Modifies the speed limit positioning in the tunnel sequence
- **LXEUNAZA** - Ramp Launch Boost  
  - Enhances the boost received from ramps

#### Score Boost
Codes that affect the game's scoring system:

- **PAUUEIAA** - 1100 Points
  - Awards 1100 points for specific actions (useful for testing scoring mechanics)
- **AAXLXSPA** - Rollover to 0
  - Causes score to rollover back to zero (demonstrates score overflow behavior)

#### Second Speed Limit Changes
Fine-tune the speed limits in racing sequences:

- **TAVNIUGA** - Speed Limit: 6
- **YAVNIUGA** - Speed Limit: 7  
- **AAVNIUGE** - Speed Limit: 8
- **PAVNIUGE** - Speed Limit: 9
- **ZAVNIUGE** - Speed Limit: 10
- **LAVNIUGE** - Speed Limit: 11
- **YAVNIUGE** - Speed Limit: 15

#### Misc Fun
Experimental codes for gameplay modification:

- **GEEZKPZA** - Increase Jump Velocity
  - Modifies the physics engine to increase jump height/distance
- **OYNAXVEV** - Reduce Gravity
  - Alters gravity constants for floating/low-gravity effects
- **PAVNGUAA** - Early Speed Limit to 1
  - Sets speed limit to 1 early in the game
- **YAVNGUAA** - Early Speed Limit to 7
  - Sets speed limit to 7 early in the game

#### Screen Wrap (broken)
**Warning**: These codes are known to cause issues:

- **TYEAUNSO** - Uh Oh
  - Attempts screen wrapping but causes glitches
- **GGEAVYAO** - Don't Do It  
  - Another broken screen wrap attempt

### Reverse Engineering Value

These Game Genie codes are particularly valuable for reverse engineering because they:

1. **Reveal Memory Addresses**: Each code targets specific memory locations, helping identify where game variables are stored
2. **Demonstrate Limits**: Show the boundaries and overflow conditions of game systems
3. **Expose Mechanics**: Reveal how different game systems (physics, scoring, speed) are implemented
4. **Aid Testing**: Allow controlled modification of game state for analysis
5. **Validate Disassembly**: Confirm understanding of code by observing the effects of memory modifications

### Using with Disassembly

When working with the Battletoads disassembly in this repository:

1. **Cross-reference codes** with the assembly source to identify the modified memory locations
2. **Test modifications** using these codes to verify understanding of game mechanics  
3. **Document findings** by comparing normal vs. modified behavior
4. **Validate patches** by implementing similar changes in the assembly source

These codes serve as a practical bridge between the theoretical disassembly work and hands-on game modification, making them an essential reference for anyone studying the Battletoads codebase.

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