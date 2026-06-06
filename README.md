# Multi-Stage Audio Amplifier Design

## Overview

This project implements a complete **multi-stage audio amplifier system** capable of amplifying low-amplitude audio signals and driving a low-impedance load. The design combines transistor amplifiers, active filtering, power amplification, and regulated power supplies to achieve high-fidelity audio amplification.

---

## Objectives

- Amplify low-level audio signals.
- Maintain signal integrity across the audio frequency range (20 Hz – 20 kHz).
- Reject common-mode noise.
- Filter unwanted frequencies.
- Drive a low-impedance load efficiently.
- Minimize distortion while maximizing output power.

---

## System Architecture

```text
Audio Input
     │
     ▼
┌─────────────────┐
│ Pre-Amplifier   │
│ Differential Amp│
└─────────────────┘
     │
     ▼
┌─────────────────┐
│ Gain Stage      │
│ CE Amplifier    │
└─────────────────┘
     │
     ▼
┌─────────────────┐
│ Band Pass Filter│
│ (20Hz–20kHz)    │
└─────────────────┘
     │
     ▼
┌─────────────────┐
│ Class AB Power  │
│ Amplifier       │
└─────────────────┘
     │
     ▼
 Speaker / Load

Power Supply:
±12V → LM7805 & LM7905 → ±5V
```

---

## Stage 1: Differential Pre-Amplifier

### Purpose

- Provides moderate voltage gain.
- Offers high input impedance.
- Rejects common-mode noise.
- Improves bias stability.

### Topology

- BJT Differential Pair
- Dual matched NPN transistors
- Shared emitter resistor
- Single-ended output

### Performance

| Parameter | Value |
|------------|--------|
| Voltage Gain | ≈ 16 |
| Collector Current | 1.5 mA |
| CMRR | ≈ 39 dB |
| Supply Voltage | ±5 V |

### Key Advantages

- Excellent noise rejection.
- Good linearity.
- Prevents overdriving subsequent stages.
- Preserves audio bandwidth.

---

## Stage 2: Common Emitter Gain Stage

### Purpose

Provides the majority of the voltage amplification required by the system.

### Topology

- Common Emitter Amplifier
- Voltage Divider Biasing
- Split Emitter Resistance
- Emitter Bypass Capacitor

### Design Features

#### DC Stability

Emitter degeneration stabilizes the operating point against temperature and transistor parameter variations.

#### AC Gain Control

The bypass capacitor removes part of the emitter resistance for AC signals, allowing high voltage gain without affecting DC bias stability.

### Performance

| Parameter | Value |
|------------|--------|
| Theoretical Gain | 30 |
| Experimental Gain | ≈ 27 |
| Input Impedance | ≈ 6 kΩ |
| Output Impedance | ≈ 10 kΩ |

### Advantages

- High voltage gain.
- Stable operating point.
- Good linearity.
- Easy integration with other stages.

---

## Stage 3: Active Band-Pass Filter

### Purpose

Passes audio frequencies while attenuating unwanted low-frequency and high-frequency components.

### Topology

- Active Band-Pass Filter
- UA741 Operational Amplifier
- Inverting Configuration

### Filter Specifications

| Parameter | Value |
|------------|--------|
| Lower Cutoff Frequency | ≈ 10 Hz |
| Upper Cutoff Frequency | ≈ 36 kHz |
| Midband Gain | 1 |

### Advantages

- Covers the entire audio spectrum.
- Prevents loading of the gain stage.
- Restores signal polarity.
- Provides frequency-selective filtering.

---

## Stage 4: Class AB Power Amplifier

### Purpose

Provides the current required to drive a low-impedance speaker load.

### Topology

- Complementary Symmetry Push-Pull Configuration
- TIP31 (NPN)
- TIP32 (PNP)
- Diode Biasing Network

### Features

#### Reduced Crossover Distortion

Two biasing diodes establish approximately 1.4 V between transistor bases, ensuring smooth transition between push and pull operation.

#### High Efficiency

Combines the efficiency advantages of Class B amplifiers with the linearity of Class A amplifiers.

#### Voltage Follower Operation

- Voltage Gain ≈ 1
- Very High Current Gain

### Performance

| Parameter | Value |
|------------|--------|
| Load Resistance | 10 Ω |
| Output Peak Voltage | ≈ 4 V |
| Output Power | ≈ 0.8 W |
| Voltage Gain | ≈ 1 |

### Advantages

- Low distortion.
- High current drive capability.
- Improved efficiency.
- Suitable for audio applications.

---

## Power Supply Section

### Voltage Regulation

| Regulator | Function |
|------------|------------|
| LM7805 | +12 V → +5 V |
| LM7905 | -12 V → -5 V |

### Benefits

- Stable supply rails.
- Low output noise.
- Improved amplifier performance.
- Better signal integrity.

---

## Simulation and Hardware Validation

The amplifier was validated through:

- LTSpice simulations.
- Breadboard implementation.
- Oscilloscope measurements.
- Function generator testing.

The experimental results closely matched the theoretical and simulation results.

---

## Performance Summary

| Metric | Result |
|----------|---------|
| Audio Band Coverage | 20 Hz – 20 kHz |
| Pre-Amplifier Gain | ≈ 16 |
| Gain Stage Gain | ≈ 27–30 |
| Band-Pass Filter Gain | 1 |
| Power Amplifier Gain | ≈ 1 |
| Output Power | ≈ 0.8 W |
| CMRR | ≈ 39 dB |
| THD @ 3 kHz | ≈ 2.2% |
| THD @ 20 kHz | ≈ 4.26% |

---

## Tools and Components Used

### Software

- LTSpice XVII

### Hardware

- Breadboard
- Oscilloscope
- Function Generator
- BC547 Transistor
- TIP31 Power Transistor
- TIP32 Power Transistor
- UA741 Operational Amplifier
- LM7805 Voltage Regulator
- LM7905 Voltage Regulator

---

## Results

The designed multi-stage audio amplifier successfully:

- Amplifies low-amplitude audio signals.
- Maintains operation across the full audio spectrum.
- Filters unwanted frequency components.
- Delivers approximately 0.8 W of power to a 10 Ω load.
- Minimizes crossover distortion using Class AB operation.
- Achieves good linearity and acceptable THD performance.

---

## Authors

- Arun Venkat Jonna
- Hemanth G

IIIT Hyderabad
