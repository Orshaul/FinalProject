# README

## Introduction
This project focuses on compressing hyperspectral images using Huffman coding, error correction with Hamming (7,4) code, and error detection using CRC (Cyclic Redundancy Check). The project integrates various components to achieve high compression rates while maintaining low error rates.

## Features
- **Hyperspectral Image Compression**:
  - Uses Huffman coding for efficient compression.
  - Supports loading the `92AV3C.lan` hyperspectral image or creating custom 3D random images.
- **Error Correction and Detection**:
  - Implements Hamming (7,4) for error correction.
  - Optionally uses CRC for error detection.
- **Error Analysis**:
  - Calculates BER (Bit Error Rate) before and after error correction.
  - Visualizes comparisons between the original, compressed, and reconstructed images.
- **Performance Optimization**:
  - Achieves computational performance within 216 nanoseconds per pixel.
- **Customizability**:
  - Choose whether to use CRC.
  - Generate random test images with adjustable dimensions.
- **Graphical User Interface (GUI)**:
  - Simplifies user interaction and visualization of results.

## Installation

### Prerequisites
- Python 3.9+
- Required libraries:
  - `numpy`
  - `matplotlib`
  - `spectral`
  - `tkinter`

Install dependencies via pip:
```bash
pip install numpy matplotlib spectral
```

### Clone the Repository
```bash
git clone <repository-url>
cd <repository-folder>
```

## Usage

### Running the Project
1. Load the hyperspectral image `92AV3C.lan` or generate a custom random image.
2. Configure the compression and error detection settings via the GUI or terminal prompts.
3. View the results including BER, compression ratio, and image visualizations.

Run the main script:
```bash
python main.py
```

### GUI Options
- **Load Image**: Load the default hyperspectral image or create a random 3D image.
- **Compression Settings**: Enable or disable CRC for error detection.
- **Visualizations**: View side-by-side comparisons of original, compressed, and reconstructed images.

## File Structure
```
├── main.py                 # Entry point of the project
├── huffman.py              # Huffman encoding and decoding functions
├── hamming.py              # Hamming (7,4) encoding and decoding functions
├── crc.py                  # CRC encoding and checking functions
├── gui.py                  # GUI implementation
├── utils.py                # Helper functions
├── README.md               # Project documentation
└── requirements.txt        # Dependencies
```

## Examples

### Example 1: Compress and Decompress an Image
1. Load the `92AV3C.lan` image.
2. Compress the image using Huffman coding.
3. Correct errors using Hamming (7,4) and CRC.
4. Reconstruct the image and compare the original vs. reconstructed version.

### Example 2: Analyze BER and Compression Ratio
- Inject random errors into the compressed data.
- Measure BER before and after Hamming correction.
- Calculate the compression ratio achieved.

## Performance
This project achieves an average processing time of **216 nanoseconds per pixel**, meeting the required computational efficiency.

## Contributing
1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Open a pull request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments
- Supervising professor and university.
- Open-source libraries and contributors.
- Hyperspectral image datasets.
