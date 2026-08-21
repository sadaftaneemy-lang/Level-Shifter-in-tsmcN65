# Level Shifter
A level shifter is a circuit that converts a digital signal from one voltage level to another while preserving the logic state.

For example:

Input: 1.2 V logic
Output: 3.3 V logic

OR

Input: 3.3 V logic
Output: 1.8 V logic

Without a level shifter, connecting circuits operating at different supply voltages can lead to incorrect logic interpretation or even damage to low-voltage devices.

## Why do we need a Level Shifter?

Modern SoCs use multiple voltage domains.


Example:


CPU Core → 0.8 V

SRAM → 1.0 V

PLL → 1.2 V

I/O Pads → 3.3 V

Since these blocks operate at different voltages, signals cannot be directly connected.


A level shifter safely transfers signals between these voltage domains

## Types of Level Shifters

There are mainly two types.

**1. Low-to-High Level Shifter (Up Shifter)**

  Input Voltage : 1.0 V

  Output Voltage : 3.3 V

This is the most commonly used level shifter.

**Purpose :** Increase voltage level.

Example

Core → GPIO

**2. High-to-Low Level Shifter (Down Shifter)**

Converts:

5 V → 3.3 V

3.3 V → 1.8 V

Example:
Input = 3.3 V HIGH
↓

Level Shifter

↓

Output = 1.2 V HIGH

## 🛠️Software

◆ Cadence Virtuoso

◆ tsmc Node65

◆ Calibre

## 🔧Components used

**Schematic**
- pch_25
- nch_25

## Typical Transistors Used

A standard CMOS level shifter usually contains:

- Two PMOS transistors (cross-coupled)
  
- Two NMOS transistors
  
- Sometimes additional enable or buffer transistors
  

The cross-coupled PMOS pair provides positive feedback, helping the output switch fully to the higher supply voltage

# 💎About the project
