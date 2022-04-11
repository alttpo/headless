# headless
A headless SNES emulator (no APU or PPU) that runs a (presumably customized) ROM, complete with CPU instruction tracing and WRAM captures.

Currently hard-coded for LoROM memory mapping.

## Usage
```
headless [options...] <rom.sfc>
  -5 string
        initialize $5000..7FFF from this file
  -d duration
        delay between CPU instructions
  -p uint
        P (processor flags) (default 52)
  -pc uint
        PC entry point; also sets program banK register (default 32768)
  -sp uint
        SP (stack pointer) (default 511)
  -t    CPU tracing
  -w string
        initialize WRAM from this file
```

The `WDM #$0A` instruction will trigger a capture WRAM to `data/%d.wram`.

The `WDM #$FF` instruction will halt execution and exit `headless`.

Memory area `$5000..7FFF` is mapped to `$3000` bytes of extra read/write RAM useful for any purpose. This is mapped only in banks with WRAM mapped in to the lower `$0000..2000` area.
