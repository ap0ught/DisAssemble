# GitHub Copilot Instructions for DisAssemble Repository

## Repository Context

This repository contains NES game disassemblies and reverse engineering tools, focusing on complete, buildable assembly source code. The primary target is the 6502 processor architecture used in the Nintendo Entertainment System (NES).

## Project Overview

- **Primary Language**: 6502 Assembly Language
- **Tools**: IDA Pro, ASM6 assembler, FCEUX emulator, custom utilities
- **Focus**: Reverse engineering, disassembly, ROM reconstruction
- **Legal Compliance**: Educational/preservation purposes, no copyrighted ROM distribution

## Coding Standards and Conventions

### Assembly Language Guidelines

1. **Syntax Style**:
   - Use lowercase for opcodes: `lda`, `sta`, `jmp`
   - Use meaningful label names: `update_player_position`, `level_data_ptr`
   - Use uppercase for constants: `SCREEN_WIDTH = $20`
   - Use snake_case for variables: `player_x`, `game_state`

2. **Memory Layout**:
   - Zero page variables: `$00-$FF`
   - Stack: `$100-$1FF`
   - RAM: `$200-$7FF`
   - ROM: `$8000-$FFFF` (depending on mapper)

3. **Code Organization**:
   ```assembly
   ; Header comment with function purpose
   ; Input: Parameters description
   ; Output: Return values description
   ; Modifies: Registers/memory affected
   function_name:
       ; Clear, concise comments
       lda #$00           ; Initialize accumulator
       sta variable       ; Store to memory
       rts
   ```

### File Organization

- **Main assembly**: `GameName.asm`
- **Data files**: `data/category.asm`
- **Graphics**: `gfx/` directory with `.chr` and compressed formats
- **Build scripts**: `BuildROM.bat`, `BuildROMWithSymbols.bat`
- **Documentation**: Memory maps in `ram_map.txt`

## Reverse Engineering Workflow

### 1. Code Analysis
- Always document memory addresses and their purposes
- Identify function entry points through interrupt vectors
- Map data structures and object layouts
- Use meaningful symbol names based on function analysis

### 2. Assembly Translation
- Maintain original program flow and logic
- Preserve exact timing-critical code sequences
- Document any deviations from original code
- Include cycle counts for timing-critical sections

### 3. Data Extraction
- Separate code from data clearly
- Use appropriate assembler directives (`.byte`, `.word`, `.include`)
- Document data formats and compression schemes
- Maintain proper alignment for graphics and sound data

## Tool-Specific Guidelines

### IDA Pro Integration
- Use `.idb` files for persistent analysis
- Apply custom scripts from `Utils/scripts/`
- Create symbol maps with meaningful names
- Document complex algorithms in comments

### ASM6 Assembler
- Use ASM6-compatible syntax
- Handle bank switching correctly for MMC mappers
- Organize code with proper `.org` directives
- Test builds frequently to catch errors early

### FCEUX Integration
- Use trace logs for execution flow analysis
- Generate CDL files for code/data identification
- Document any emulator-specific behaviors

## Code Quality Requirements

### Documentation Standards
1. **Function Headers**: Every function must have purpose, parameters, and side effects documented
2. **Data Structures**: Comment field purposes and layouts
3. **Complex Logic**: Step-by-step explanations for intricate algorithms
4. **Memory Maps**: Maintain accurate RAM usage documentation

### Testing and Validation
1. **Build Verification**: Ensure assembly produces identical ROM checksums
2. **Functional Testing**: Verify gameplay behavior matches original
3. **Cross-Reference**: Compare with IDA analysis for accuracy
4. **Edge Cases**: Test boundary conditions and error scenarios

## Legal and Ethical Guidelines

### Copyright Compliance
- **NO ROM FILES**: Never include copyrighted ROM images
- **Source Only**: Provide only disassembled source code
- **Fair Use**: Educational and preservation purposes only
- **Attribution**: Credit original developers where appropriate

### Documentation Requirements
- Include legal notices about ROM acquisition requirements
- Document reverse engineering methodologies
- Maintain clear boundaries between analysis and original content
- Respect intellectual property rights

## Technical Constraints

### NES Hardware Limitations
- **Memory**: Limited RAM (2KB internal + cartridge)
- **Banking**: Handle MMC mappers correctly
- **Timing**: Respect PPU/APU timing constraints
- **Architecture**: 6502 processor limitations (no stack-relative addressing)

### Assembler Limitations
- ASM6 syntax requirements and capabilities
- Label scope and forward reference handling
- Binary data inclusion methods
- Cross-platform compatibility considerations

## Common Patterns

### Memory Management
```assembly
; Zero page variable declaration
player_x = $10
player_y = $11
temp_var = $20

; RAM structure documentation
; Object structure (8 bytes per object):
; +0: X position
; +1: Y position
; +2: Sprite ID
; +3: Status flags
object_array = $0300
```

### Data Tables
```assembly
; Level configuration table
level_data:
    .word level_1_map, level_1_attr
    .word level_2_map, level_2_attr
    ; ... additional levels

level_1_map:
    .byte $01, $02, $03  ; Tile data
    .byte $00            ; End marker
```

### Bank Switching (MMC3)
```assembly
; Switch to bank N
lda #bank_number
sta $8000           ; Bank select
sta $8001           ; Bank data
```

## Error Prevention

### Common Pitfalls
1. **Address Mode Confusion**: Be explicit about addressing modes
2. **Bank Boundary Issues**: Check for code crossing bank boundaries
3. **Timing Dependencies**: Document cycle-accurate requirements
4. **Data Alignment**: Ensure proper byte/word alignment

### Best Practices
1. **Incremental Development**: Build and test frequently
2. **Version Control**: Commit working states regularly
3. **Cross-Platform**: Consider Windows/Linux compatibility
4. **Documentation**: Write comments as you reverse engineer

## Repository-Specific Notes

### Battletoads Specifics
- Uses MMC1 mapper with 16KB PRG banks
- Complex compression for graphics (`.4` format)
- Multiple difficulty levels affect gameplay logic
- Sound engine integration with gameplay timing

### Tool Integration
- Use `bt_unpack_4.exe` for graphics decompression
- Apply `HardwiredBank.idc` for fixed bank analysis
- Reference `ram_map.txt` for memory layout
- Check `README.dev` for detailed workflows

## Getting Started Checklist

When contributing to this repository:

1. **Environment Setup**:
   - [ ] IDA Pro with NES loaders configured
   - [ ] ASM6 assembler available
   - [ ] FCEUX emulator installed
   - [ ] Hex editor for binary analysis

2. **Code Standards**:
   - [ ] Follow assembly naming conventions
   - [ ] Include comprehensive function documentation
   - [ ] Test build process thoroughly
   - [ ] Verify ROM functionality in emulator

3. **Legal Compliance**:
   - [ ] Ensure no copyrighted material included
   - [ ] Document reverse engineering methodology
   - [ ] Include appropriate legal notices
   - [ ] Respect fair use guidelines

This repository maintains the highest standards for reverse engineering documentation and legal compliance. All contributions should advance the educational and preservation goals while respecting intellectual property rights.