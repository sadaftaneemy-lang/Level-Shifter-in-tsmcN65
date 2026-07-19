# Level Shifter
A level shifter is a circuit that converts a digital signal from one voltage level to another while preserving the logic state.

For example:

Input: 1.2 V logic
Output: 3.3 V logic

OR

Input: 3.3 V logic
Output: 1.8 V logic

Without a level shifter, connecting circuits operating at different supply voltages can lead to incorrect logic interpretation or even damage to low-voltage devices.

# Why do we need a Level Shifter?

Modern SoCs use multiple voltage domains.

Example:

CPU Core → 0.8 V
SRAM → 1.0 V
PLL → 1.2 V
I/O Pads → 3.3 V

Since these blocks operate at different voltages, signals cannot be directly connected.

A level shifter safely transfers signals between these voltage domains
