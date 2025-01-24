

[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/release/python-380/)
[![MIT License](https://img.shields.io/badge/license-MIT-green)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/status-Active-success)](#)


# **קידוד משולב מקור/ערוץ של חישה היפר-ספקטראלית**
תקציר
פרויקט זה עוסק בפיתוח אלגוריתם לדחיסת תמונה היפרספקטראלית ולתיקון שגיאות בערוץ לווייני רועש. אוניברסיטת תל-אביב מפתחת לוויין זעיר למחקר אקלים וסביבה. האלגוריתם מיועד לננו-לוויין שיצויד במצלמה היפר-ספקטראלית המאפשרת צילום במספר אורכי גל לצורך זיהוי חתימות ספקטראליות של מזהמים באטמוספירה ועל הקרקע. רוחב הסרט המוגבל וזמן החליפה הקצר מעל תחנת הקרקע מחייבים דחיסת המידע בחלל לפני שידורו לכדור הארץ. מצד שני, דחיסת המידע מגדילה את רגישותו לשגיאות ועלולה לגרום לשגיאה קטסטרופאלית במהלך הפיענוח על הקרקע. האלגוריתם שלנו מאפשר שליטה בפרמטרים שונים של הדוחס ושל הצופן לתיקון שגיאות בהתאם לחשיבות המידע הנדחס, על מנת להגיע לאופטימיזציה של קריטריון ביצועים משולב של דחיסה מצד אחד ועמידות לשגיאות מצד שני בתנאי הסתברות שגיאה שונים בערוץ הלווייני בו משודר המידע מהלוויין לכדוה"א. ביצועי האלגוריתם נבחנו על גבי בסיס נתונים של לווייני חישה מרחוק. בשלב הראשון בפרויקט התמקדנו בהגעה ליחס הדחיסה הנדרש 1:4 כאשר הערוץ אינו רועש. כלומר, חישבנו את הפרדיקטור לכל פיקסל בתמונה, המסתמך על פיקסלים שכנים. לאחר מכן, הפעלנו קוד האפמן על סדרת ההפרשים בין כל פיקסל לפרדיקטור המתאים לו ובכך מימשנו דחיסה חסרת עיוות, לא הפסדית המאפשרת שחזור מלא של המידע המקורי. בשלב השני כתבנו אלגוריתם לתיקון שגיאות באמצעות קוד האמינג (7,4) עם בדיקת CRC אופציונלית בהסתברות שגיאה המוגדרת בדרישות הכמותיות לפרויקט. קיבלנו עמידה בדרישות הכמותיות שהן: יחס דחיסה 1:4 או טוב יותר, יחס השגיאות לביט (שיעור השגיאות או BER) נמוך מ-10^(-5) לאחר תיקון, וזמן עיבוד ממוצע לפיקסל של 216 ננו-שניות או פחות. לבסוף, החלטנו לפתח ממשק משתמש גרפי (GUI) ליצירת כלי תכנון המספק ממשק נוח עם אפשרות לבחירת פרמטרים שונים כגון: גודל התמונה, שיעור שגיאות (BER), ושימוש אופציונלי בקוד CRC. ממשק זה מאפשר לחוקר להריץ באופן יעיל את הסימולטור בתרחישים שונים של בחירת פרמטרים ולהסיק מסקנות בנוגע לתכנון מערכת מבצעית. 





<p align="center">
<img src="diagram.png" alt="Workflow Diagram" width="800">
</p>


---

### **Table of Contents**
1. [Overview](#project-overview)
2. [Features](#key-features)
3. [Setup](#setup)
4. [Usage](#usage)
5. [Results](#results-and-evaluation)
6. [Citing This Work](#citation)

---

## **Project Overview**
This project implements a **combined source/channel coding system** for compressing and error-correcting hyperspectral images. The system incorporates **Huffman encoding**, **Hamming (7,4) error correction codes**, and **Cyclic Redundancy Check (CRC)** for validation. A GUI application is included to allow users to load or create images, select parameters, and visualize results.

### **Key Features**:
- Hyperspectral image compression using Huffman coding.
- Error correction via Hamming (7,4) codes.
- Data validation using CRC.
- Supports custom or preloaded hyperspectral images.
- Graphical User Interface (GUI) for user interaction.
- Quantitative evaluation of compression ratio, Bit Error Rate (BER), and computational complexity.

---

### **Setup**

Clone the repository and install dependencies:
```bash
git clone https://github.com/your-repo/project-name.git
cd project-name
pip install -r requirements.txt
```

Launch the application:
```bash
python main.py
```

---

## **Usage**
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

## **Results and Evaluation**
#### Compression Ratio and BER
- **Compression Ratio:** Achieves better than 1:4 in most cases.
- **Bit Error Rate:** Maintains BER below \(10^{-5}\).

#### Visualization:
Original, compressed, and reconstructed images are displayed for analysis.

| Original Image | Compressed Differences | Reconstructed Image |
|----------------|-------------------------|----------------------|
| ![Original](https://via.placeholder.com/150?text=Original) | ![Compressed](https://via.placeholder.com/150?text=Compressed) | ![Reconstructed](https://via.placeholder.com/150?text=Reconstructed) |

---

## **File Structure**
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

## **Key Functions**
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

## **Citation**
If you find this project helpful, please consider citing:

```bibtex
@article{your_citation,
  title={Combined Source/Channel Coding for Hyperspectral Sensing},
  author={Your Name, Collaborator Names},
  journal={Journal Name},
  year={2025},
  publisher={Your Institution}
}
```

---

## **Acknowledgments**
Special thanks to the developers of the [Huffman library](https://github.com/username/huffman) and [Spectral Python](http://www.spectralpython.net/).

---

