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

### Overall Framework

- **Transmitter**: Includes the generation of data, encoding, modulation, and OFDM signal synthesis.
- **Channel**: Represents the medium over which the OFDM signals travel, characterized by multipath fading and noise.
- **Receiver**: Comprises synchronization, channel estimation, demodulation, decoding, and error-checking stages.

A detailed diagram of the framework can be found below:

![OFDM System Framework](https://github.com/JiaqiTu/OFDM-wireless-communication-system/blob/main/diagrams/Simulink%20Model%20visulization%20for%20OFDM.png)

Following this high-level overview, we dive into each component's specific implementation details.

### 1. Baseband Data Generation

- **Module Used**: Bernoulli Random Number Generator from the Simulink library.
- **Function**: Generates random binary numbers with a probability of 0.5 for both '0' and '1'.
- **Output**: Data is outputted in frames, with each frame containing 20 binary digits.

### 2. Adding CRC Redundancy

- **Module Used**: CRC Generator from the Simulink library.
- **Function**: Employs a 24th-order CRC generator polynomial to each data frame.
- **Output**: Processes each 20-bit data frame and appends 24 redundant CRC bits, resulting in 44-bit frames.

### 3. Turbo Encoding and Interleaving

- **Process Flow**:
  - The original bit sequence is divided into two pathways.
  - One path inputs directly into a Convolutional Encoder.
  - The second path passes through a Random Interleaver before entering another Convolutional Encoder (labeled Convolutional Encoder1).
  - A Deinterleaver separates the outputs from the two encoders into odd and even bit sequences.
  - The odd sequences from the first Convolutional Encoder and the even sequences from both Convolutional Encoders are merged using a Multiplexer (Mux).
  - The resulting serial sequence is the output of the Turbo encoding process.
  - Data interleaving and the pruning of redundant bits are then performed to finalize the encoded data stream.

### 4. 16-QAM Modulation
Modulates the encoded data using 16-Quadrature Amplitude Modulation (16-QAM), which translates bits into complex symbols for amplitude and phase representation, preparing the data for channel transmission.


### 5. OFDM Modulation and Demodulation

OFDM modulation in Simulink is accomplished by utilizing the platform's row and column selection tools to appropriately insert different data into 64 IFFT points. Following this, a cyclic prefix is added at the end of the data block, and the OFDM-processed data is inserted at the beginning of the transmission frame.

#### Pilot Signal Insertion

The insertion of pilot signals adopts a block-type structure. Within a specific OFDM symbol, all the signals are pilot signals. These pilot signals are periodically transmitted, which is an approach that is especially suitable for slow-fading channels. Given that in such a symbol, all sub-carriers are occupied by pilot signals, there is no need for channel interpolation in the frequency direction, which makes the system less sensitive to frequency-selective fading.

<img src="https://github.com/JiaqiTu/OFDM-wireless-communication-system/blob/main/diagrams/ofdm_sig1.png" width="500" height="300" alt="OFDM signal">


#### OFDM Demodulation

The demodulation of OFDM is the reverse procedure of modulation. It starts with the removal of the cyclic prefix and is followed by performing an FFT transform. After the FFT, the data that has been subject to channel fading is extracted at the original positions of the transmitted data.



## Testing and Results



