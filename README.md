# libwally for Arduino and Mbed

## About this library

[libwally](https://github.com/ElementsProject/libwally-core/) is an bitcoin library developed and maintained by [Blockstream](https://blockstream.info/). It is used in many projects like Green Wallet, C-Lightning and others, so it's really well maintained and tested in real projects.

This repository introduces a few hacks for Arduino and Mbed build systems that allows you to use the library out of the box.

As you see `libwally-core` is included as a submodule, and the `src` folder only contains aliases to the original files of the library. These files are generated by `build.py` script. It results in a huge mess in `src/` folder, but it works!

Tested on ESP32 (M5Stack, TTGO) and STM32F469I-Discovery (Mbed OS - bare metal, no RTOS).

## Installation

### For Arduino:

Clone this repo with `--recursive` flag to the `Arduino/libraries/` folder (or download zip file and select `Sketch->Include Library->Add .ZIP Library`. Check out the [example](examples/wally_example/wally_example.ino) to see it in action.

Make sure you have [secp256k1](https://github.com/diybitcoinhardware/secp256k1-embedded) library installed. In your sketch add `#include <secp256k1>` even if you are not using - this will force Arduino IDE to copy secp256k1 library to the build folder as well.

### For Mbed:

[DOESNT WORK YET]

Clone this repo with `--recursive` flag to the project folder, or whatever folder you store libraries in. In the online IDE do `Import Library` and put there a link to this repository.

Check out the [example](examples/mbed/main.cpp). You can also import [this project](https://os.mbed.com/users/diybitcoinhardware/code/libwally_example/) and start from there.

**Important!** Library mostly uses stack, and mbed has pretty small default limitat for the stack size. You can increase the stack size in `mbed_app.json` file:

```json
{
    "target_overrides": {
        "*": {
            "rtos.main-thread-stack-size": "8192"
        }
    }
}
```

Or you can use bare-metal mbed version:

```json
{
	"requires": ["bare-metal"]
}
```

## Usage

A very basic example:

```cpp
TODO
```