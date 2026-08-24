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

**3. Bidirectional Level Shifter**

Works in both directions automatically.

Used for communication protocols such as:

- I²C
- SMBus
- One-Wire

## Where are Level Shifters Used?

They are common in:

- VLSI chips
- Microcontrollers
- Processors
- Memories
- SoCs (System-on-Chip)
- Mobile processors
- Mixed-voltage digital systems

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

In this circuit, there are two supply domains:

VDD1 → Low-voltage domain

VDD2 → High-voltage domain

GND → Common ground

VIN → Input signal

VOUT → Level-shifted output

**The basic purpose is :** Convert a logic signal referenced to VDD1 into a logic signal referenced to VDD2.

For example :

**Input domain:**

0 V → VDD1 = 1.2 V

**Output domain:**

0 V → VDD2 = 2.5 V

Therefore:
The important point is that the input voltage does not need to reach VDD2. The circuit uses VDD2 to generate the high-voltage output

## 2. Why Do We Need a Level Shifter?

Suppose one block of an IC operates at 1.2 V and another block operates at 2.5 V.

If the 1.2 V signal is directly connected to a circuit expecting a 2.5 V logic signal, several problems can occur:

The HIGH level may not be sufficient for the receiving circuit.
The receiving transistors may not switch properly.
Noise margins can be reduced.
High-voltage devices may require appropriate gate voltages.
Direct connection can result in incorrect logic operation.

Therefore, a level shifter acts as an interface:

```
Low-voltage block

      │
      
      │  VDD1-domain signal
      
      ▼
      
  LEVEL SHIFTER
  
      │
      
      │  VDD2-domain signal
      
      ▼
      
High-voltage block
```
## 3. Overall Structure of Your Circuit

Your schematic can be divided into three major sections:

Block 1 — Input inverter

Consists of:

PMOS1
NMOS1
Block 2 — Core level-shifting stage

Consists of:

- PMOS2
  
- PMOS3
  
- NMOS2
  
- NMOS3
  

This is the most important section.

Block 3 — Output buffer


Consists of:

- PMOS4 + NMOS4
- 
- PMOS5 + NMOS5

These are two CMOS inverter stages used to buffer and restore the signal.

So conceptually:






