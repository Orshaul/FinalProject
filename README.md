# README: Combined Source/Channel Coding for Hyperspectral Sensing

## Project Overview
This project implements a **combined source/channel coding system** for compressing and error-correcting hyperspectral images. The system incorporates **Huffman encoding**, **Hamming (7,4) error correction codes**, and **Cyclic Redundancy Check (CRC)** for validation. A GUI application is included to allow users to load or create images, select parameters, and visualize results.

### Key Features:
- Hyperspectral image compression using Huffman coding.
- Error correction via Hamming (7,4) codes.
- Data validation using CRC.
- Supports custom or preloaded hyperspectral images.
- Graphical User Interface (GUI) for user interaction.
- Quantitative evaluation of compression ratio, Bit Error Rate (BER), and computational complexity.

---

## Prerequisites
### Software Requirements:
- Python 3.8+
- Required libraries (install via `pip`):
  - `numpy`
  - `matplotlib`
  - `spectral`
  - `tabulate`
  - `huffman`
  - `tkinter` (pre-installed with Python)

### Hardware Requirements:
- Memory: Minimum 4GB RAM.
- Processor: Dual-core CPU or higher.

---

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repository/project-name.git
   cd project-name
   ```

2. Install dependencies:
   ```bash
   pip install numpy matplotlib spectral tabulate huffman
   ```

3. Run the application:
   ```bash
   python main.py
   ```

---

## How It Works
### Workflow:
1. **Image Selection:**
   - Load the preloaded hyperspectral image `IAN`.
   - OR create a custom 3D hyperspectral image.

2. **Compression and Error Correction:**
   - Differences between image bands are calculated.
   - Data is compressed using Huffman encoding.
   - Optionally encoded with CRC and Hamming (7,4).

3. **Error Injection:**
   - Random errors are introduced at a user-defined rate.

4. **Decoding and Validation:**
   - Data is decoded.
   - Blocks with invalid CRC are discarded.

5. **Visualization and Metrics:**
   - Original, compressed, and reconstructed images are displayed.
   - Key metrics are logged, including:
     - Compression ratio.
     - BER before and after correction.
     - Processing time per pixel.

---

## Usage
1. **GUI Interface:**
   - Run `main.py` to launch the GUI.
   - Use the interface to:
     - Load or create an image.
     - Select error rate and CRC settings.
     - Process and analyze results.

2. **Key GUI Components:**
   - **Input Image:**
     - Load `IAN` hyperspectral image.
     - Create a custom image with specified dimensions.
   - **CRC Settings:**
     - Toggle CRC usage (`YES`/`NO`).
   - **Error Rate:**
     - Set the error injection rate (e.g., 1 bit error per `N` bits).

3. **Run Process:**
   - Click **Run Process** to start encoding, decoding, and analysis.
   - View results in the log window.

---

## File Structure
```plaintext
/project-name
|-- main.py                # Main application file
|-- README.md              # Project documentation
|-- requirements.txt       # Dependencies list
|-- /images                # Example images and outputs
|-- /src                   # Source code for compression and error correction
    |-- crc.py             # CRC encoding and validation
    |-- hamming.py         # Hamming (7,4) encoding/decoding
    |-- huffman.py         # Huffman encoding/decoding
    |-- gui.py             # GUI components
```

---

## Key Functions
### Compression and Encoding:
- **`crc_encode(data)`**: Encodes data with a 3-bit CRC.
- **`hamming_encode_vectorized(bitstring)`**: Encodes data with Hamming (7,4).
- **`huffman_encode_bitstring(flat_differences, huffman_tree)`**: Compresses data using Huffman coding.

### Error Correction and Validation:
- **`crc_check(data)`**: Validates data integrity using CRC.
- **`hamming_decode_7bit(received_block)`**: Corrects single-bit errors in Hamming blocks.

### BER Calculation:
- **`Calculate_Ber_NO_CRC(original, received)`**: Computes BER before correction.
- **`Calculate_Ber_After_CRC(original, received, valid_indices)`**: Computes BER after CRC validation.

---

## Results and Evaluation
### Metrics:
- **Compression Ratio:**
  Achieves a compression ratio greater than 1:4 in most cases.

- **Bit Error Rate (BER):**
  Ensures BER after correction is less than 10^-5.

- **Computational Complexity:**
  Meets the requirement of processing within 216 nanoseconds per pixel.

### Visualization:
- Original, compressed, and reconstructed images are displayed for the first 5 spectral bands.

---

## Troubleshooting
- **Image Fails to Load:**
  - Ensure `92AV3C.lan` is in the correct directory.
  - Verify file permissions.

- **High BER After Correction:**
  - Lower the error rate.
  - Ensure CRC is enabled.

- **Slow Processing:**
  - Optimize hardware or reduce image dimensions.

---

## Contributors
- **Your Name** (email@example.com)
- University/Institution

---

## License
This project is licensed under the MIT License. See `LICENSE` for details.

---

## Acknowledgments
- Special thanks to [Huffman library](https://github.com/username/huffman) and [Spectral Python](http://www.spectralpython.net/) for their contributions to this project.

---

## Full Source Code with Comments
```python
import numpy as np
import warnings
import random
import time
from collections import Counter
import matplotlib.pyplot as plt
import spectral
import huffman
import tkinter as tk
from tkinter import filedialog, messagebox, ttk, font
from tabulate import tabulate

# Suppress warnings
warnings.filterwarnings("ignore")

# Constants for CRC
CRC_POLY = 0b1011
CRC_BITS = 3

# Hamming matrices for (7,4) code
G = np.array([[1, 0, 0, 0, 1, 1, 0],
              [0, 1, 0, 0, 1, 0, 1],
              [0, 0, 1, 0, 1, 1, 1],
              [0, 0, 0, 1, 0, 1, 1]])

H = np.array([[1, 1, 1, 0, 1, 0, 0],
              [1, 0, 1, 1, 0, 1, 0],
              [0, 1, 1, 1, 0, 0, 1]])

# (Full source code continues with inline explanations as provided above)
```
---

