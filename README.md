# OFDM-wireless-communication-system

## Introduction
Shanghai University Broadband wireless communication course project

This project is an in-depth exploration of implementing an Orthogonal Frequency-Division Multiplexing (OFDM) wireless communication system with MATLAB Simulink. 

## Design Requirements

1. **Transmitter Design & Implementation**: This includes the generation of training sequences and pilots, cyclic prefix addition, modulation, and encoding.
2. **Receiver Synchronization**: Implementation of timing, symbol, and sampling frequency synchronization.
3. **Channel Estimation**: Techniques for estimating the communication channel characteristics.
4. **Receiver Equalization, Demodulation & Decoding**: The process of adjusting the receiver to counteract the signal distortion, demodulate, and decode the received signal.

#### Knowledge Points

The project may cover the following concepts:
1. **OFDM Transmission Principles**: Understanding of FFT, IFFT, and multi-carrier transmission methods.
2. **Digital Modulation Techniques**: Such as 16-QAM and others.
3. **Channel Coding**: Group codes, convolutional codes, and their applications.
4. **Interleaving and Channel Equalization**: Methods to reduce errors and distribute signal distortions.
5. **Synchronization Algorithms**: Algorithms for ensuring the receiver is in sync with the transmitter signal.

## OFDM Principles

OFDM, short for Orthogonal Frequency Division Multiplexing, is a form of multi-carrier modulation technique. It operates by transmitting multiple streams of data simultaneously over many orthogonal carriers. These carriers are sinusoidal waves at different frequencies, each orthogonal to the others, thus minimizing interference.

Key advantages of OFDM include:
- **High Spectral Efficiency**: By overlapping the carriers, OFDM makes efficient use of the available bandwidth.
- **Robustness Against Multipath Fading**: OFDM reduces the risk of multipath interference, which is common in wireless communication.
- **Mitigation of ISI and ICI**: It effectively suppresses Inter-Symbol Interference (ISI) and Inter-Carrier Interference (ICI), improving the clarity of the received signal.

## Technologies Used
Key technologies integrated into this project include:
- Protection Interval
- Interleaving
- CRC Check
- Turbo Coding/Decoding
- QAM Modulation

## Implementation Process
The project follows a structured implementation process, starting from signal encoding to modulation and transmission.

## Testing and Results



