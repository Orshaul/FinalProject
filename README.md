# README

## Introduction
This project is focused on compressing hyperspectral images using Huffman coding for efficient compression, Hamming (7,4) for error correction, and CRC (Cyclic Redundancy Check) for error detection. The system integrates these coding methods to achieve a high compression ratio while maintaining minimal error rates. The final implementation includes a GUI for easy interaction and visualization.

## How to Run the Project

### Prerequisites
- Python 3.9+
- Required libraries:
  - numpy
  - matplotlib
  - spectral
  - tkinter
  - tabulate

Install dependencies using pip:
```bash
pip install numpy matplotlib spectral tabulate
```

### Running the Code
1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-folder>
```
2. Run the `main.py` file:
```bash
python main.py
```
3. Use the GUI to:
   - Load the hyperspectral image `92AV3C.lan` or create a custom 3D random image.
   - Select CRC usage (`YES` or `NO`).
   - Input the desired error rate.
   - Click `Run Process` to start the compression and decoding process.

## Code Explanation

### Imports and Constants
- `numpy`, `warnings`, `random`, `time`: For numerical operations, warnings, randomness, and timing.
- `matplotlib.pyplot`, `spectral`: For visualization and hyperspectral image handling.
- `tkinter`, `tabulate`: For the GUI and results display.
- **Constants**:
  - `CRC_POLY` and `CRC_BITS`: Define the polynomial and bit length for CRC.
  - `G` and `H`: Matrices for Hamming (7,4) encoding and decoding.

### Core Functions

#### CRC Functions
- `crc_encode(data)`: Appends CRC bits to the input data for error detection.
- `crc_check(data)`: Validates the integrity of data using the CRC polynomial.

#### Hamming Functions
- `hamming_encode_vectorized(bitstring)`: Encodes data using the Hamming (7,4) code.
- `hamming_decode_7bit(received_block)`: Decodes a 7-bit block and corrects single-bit errors.

#### Combined CRC and Hamming
- `crc_hamming_encode(bitstring)`: Combines CRC and Hamming encoding.
- `crc_hamming_decode_and_validate(received_bitstring)`: Decodes and validates blocks using CRC and Hamming.

#### Error Injection
- `introduce_errors(encoded_bitstring, error_rate)`: Simulates random bit errors in the encoded data.

#### BER Calculation
- `Calculate_Ber_NO_CRC(original, received)`: Computes the Bit Error Rate without CRC.
- `Calculate_Ber_After_CRC(original, received, valid_indices)`: Computes BER after validating blocks with CRC.

#### Predictor and Huffman Coding
- `calculate_predictor(image)`: Predicts pixel values based on neighbors for compression.
- `huffman_encode_bitstring(flat_differences, huffman_tree)`: Encodes differences using Huffman coding.
- `huffman_decode_bitstring(encoded_data, huffman_tree)`: Decodes Huffman-encoded data.

### GUI Implementation

#### Main Functions
- `load_image()`: Loads the hyperspectral image `92AV3C.lan`.
- `create_custom_image()`: Generates a custom 3D image with user-specified dimensions.
- `run_process()`: Main processing pipeline:
  - Computes differences using the predictor.
  - Encodes differences using Huffman, CRC, and/or Hamming based on user selection.
  - Injects errors and calculates BER before and after correction.
  - Displays results including BER, compression ratio, and images.

#### Helper Functions
- `display_images(image, differences, decompressed_image)`: Visualizes original, compressed, and decompressed images.
- `update_status(message, bold=False)`: Updates the GUI status bar.
- `log_output(message, ...)`: Logs messages in the GUI.

### Running the GUI
The GUI provides a user-friendly interface to load images, configure parameters, and view results. Key elements include:
- Dropdown for selecting CRC usage.
- Input fields for error rate and custom image dimensions.
- Buttons for running the process and clearing logs.
- Status bar for real-time updates.

### Quantitative Results
- Compression Ratio: Displayed in the GUI log.
- BER Before and After Correction: Calculated and shown in the log.
- Time per Pixel: Computed and validated against the 216 ns/pixel requirement.

### Visualization
- Side-by-side comparison of original, compressed, and decompressed images.

### Final Remarks
The project integrates source and channel coding techniques to demonstrate effective compression and error correction for hyperspectral sensing. Use the GUI for seamless interaction and analysis.
