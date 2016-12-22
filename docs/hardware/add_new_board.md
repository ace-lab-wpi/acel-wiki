# Add a New Board Type

Here are the steps to add a new hardware target. This assumes that the CPU architecture is supported already.

For an overview of the software architecture please [read this](Development-Firmware-Architecture-Overview)

## Firmware code changes

The changes you will need to make for your target should be largely confined to the `flight/targets/<board name>` directory, which you will need to create. It is probably easiest to start by copying a directory of a board most similar to yours.
* if you are doing an F1 board, start with `flight/targets/coptercontrol`
* if you are doing an F3 board, start with `flight/targets/sparky`
* if you are doing an F4 board, start with `flight/targets/quanton`
and copy that file to your `flight/targets/<board name>` where `<board name>` is what you want to call your new target.

### Main Makefile

`flight/targets/<board name>/fw/Makefile`

Add your board name (lowercase) to the "ALL_BOARDS" variable
Add your board name (capitalised) to the Friendly names variable
If necessary, exclude your board from the boot loader updater targets.


### Board-level definitions

Before being able to compile a firmware for this board, you have to configure the build environment so that the PiOS HAL is mapped to the way the MCU peripherals are configured on your target, how memory is mapped, how the target is programmed, etc.

#### Update the `board-info.mk` file

`./flight/targets/<board name>/board-info/board-info.mk`

This file defines the actual hardware chip used by the board, memory mapping, CPU frequency and programming methods. It also contains PiOS-related: board model, revision, type.

This contains a lot of the meta information for your target that is packaged into the boot loader and determines details about the memory layout, as well as the unique board ID. For the board id (BOARD_TYPE) make sure you are not conflicting with the [existing targets](Development-Hardware-IDs).

### Board hardware description and power initialization code

`flight/targets/<board name>/board-info/board_hw_defs.c`

This is one of the most important files for your target, and contains the majority of the hardware mappings. See other examples for the conventions. It is used by both the main firmware and the bootloader.

`flight/targets/<board name>/fw/pios_board.c`

This file is the one that predominantly uses `board_hw_defs.c` to power up the board and contains most of the remainder of the board specific information.

### Add your target to the boards.h file

`flight/PiOS/inc/pios_board_info.h`

add a board define for your board (for instance STM32F4xx_Revolution.h)
update pios_board.h to include this define.

This file is largely historical and more information has been migrating to `board_hw_defs.c` and `pios_board.c`, but still contains various defines for the various peripherals of the MCU are configured for this target (used by the PiOS drivers):
   - Bootloader Settings
   - LED defines
   - SPI
   - Watchdog
   - I2C
   - Serial ports
   - USB

It also contains application settings such as:
   - Temetry stack
   - RC Receiver settings (channels, protocols)

It defines low-level hardware configuration specific to the board:
   - Clocks, IRQ, DMA

### Bootloader

If the other files are changed properly, no changes should be needed here.

## Getting your target into the main code base

There are a number of requirements for adding a target to the main repository:

1. clean implementation consistent with the changes above
1. person willing to maintain that target if there are problems
1. have your unique board ID added to the [list of targets](Development-Hardware-IDs)
1. open source hardware with the hardware files included in `flight/target/<board name>/hw`

Once those requirements are met, upload your code to github and [create a pull request](https://help.github.com/articles/creating-a-pull-request).

If you are unsure of things, feel free to upload your code and either point us to it on the forums or create a pull request and ask questions.
