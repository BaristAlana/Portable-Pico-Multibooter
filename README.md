# Pico multiboot loader

This is a quick project to make a portable GBA multiboot distributor using a Raspberry Pico.

The multiboot rom is built into the pico.

If you want something less portable, but more flexible, consider these projects:

- [Pico passthrough for your computer to talk with your GBA](https://github.com/zaksabeast/Raspberry-Pico-GBA-Passthrough)
- [Web app that uses a passthrough to multiboot any rom and manage save](https://github.com/zaksabeast/Web-GBA-multibooter-and-save-manager/tree/save-in-browser)

## Running

1. Copy your multiboot rom to `mb.gba` in the repo directory
2. Hold the pico reset button
3. Connect it to the computer
4. Run `cargo run --release`
5. Eject and reset the pico
6. Plug the pico into the GBA
7. Turn on the GBA

## Connecting a pico to a GBA

If you look at a Gameboy or Gameboy advance link cable you'll see something similar to this:

```
      /---\
 /-------------\
/ -1-  -3-  -5- \
|               |
\ -2-  -4-  -6- /
 \-------------/
```

Pin description:

1. Vcc
2. GBA Tx, Adapter Rx
3. GBA Rx, Adapter Tx
4. Reset
5. Clk
6. Gnd

Connecting to the pico:

- GBA pin 6 to Pico pin 3 (Gnd <-> Gnd)
- GBA pin 5 to Pico pin 4 (Clk <-> Clk)
- GBA pin 3 to Pico pin 5 (Rx <-> Tx)
- GBA pin 2 to Pico pin 6 (Tx <-> Rx)
- GBA pin 4 to Pico pin 7 (CS/Reset <-> unused)

## Credits

Created from the [rp2040 project template](https://github.com/rp-rs/rp2040-project-template).

Thanks to these projects for being good references:

- https://github.com/tangrs/usb-gba-multiboot
- https://problemkaputt.de/gbatek.htm
