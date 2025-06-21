
# 🔐 Encryption-Based Image Steganography

This project implements a secure steganography system that hides encrypted messages inside images using AES encryption and XOR-based pixel embedding. The approach ensures confidentiality while preserving the visual quality of the image.

---

## 🧠 Project Objective

To develop a method that allows secure and hidden transmission of sensitive text data through digital images, using encryption to protect the content and image embedding to hide its existence.

---

## 🚀 Features

- AES (CBC mode) encryption for secure data protection.
- XOR-based byte embedding into image pixel values (RGB).
- Maintains original image quality with imperceptible modifications.
- Key-based access control for encryption and decryption.
- Works with lossless image formats like `.png` and `.bmp`.

---

## 🖥️ System Requirements

- Python 3.7+
- RAM: Minimum 4 GB
- OS: Windows/Linux/macOS
- Input Image: `.png` or `.bmp` recommended

---

## 📦 Required Libraries

Install using pip:
```bash
pip install opencv-python pycryptodome numpy
```

---

## 📁 Project Structure

```
steganography-project/
├── encrypt_stegano.py       # Main script for encryption & hiding
├── input.jpg                # Source image
├── encrypted_output.png     # Image with hidden encrypted data
├── README.md
```

---

## ⚙️ How to Run

1. Place your source image in the project directory as `input.jpg`.
2. Edit the `text` and `key` values in `encrypt_stegano.py`.
3. Run the script:
```bash
python encrypt_stegano.py
```
4. It will generate `encrypted_output.png` with the hidden message.
5. Re-run the script and re-enter the same key when prompted to decrypt.

---

## 🔐 How It Works

1. **Encryption**: The text is encrypted using AES (CBC mode), with a SHA-256-derived key.
2. **XOR Encoding**: Each byte of the encrypted message is XORed with characters from the key.
3. **Image Embedding**: The XORed bytes are embedded into RGB pixel values.
4. **Extraction**: Bytes are extracted from the image using the same key.
5. **Decryption**: AES is used to convert the byte stream back into readable text.

---

## 📌 Limitations

- Works best with small text messages and high-resolution images.
- Requires exact key to decrypt; no key recovery support.
- Doesn’t support compressed formats like `.jpg` due to quality loss.

---

## 🔮 Future Scope

- Support for other file types (e.g., PDF, audio).
- GUI or web interface integration (Tkinter, Flask, React).
- LSB embedding + AES hybrid techniques.
- Steganalysis detection and anti-detection modules.

---

## 📚 References

- [OpenCV Docs](https://docs.opencv.org)
- [PyCryptodome](https://www.pycryptodome.org/)
- [AES Standard (FIPS 197)](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- [SHA-256 - Wikipedia](https://en.wikipedia.org/wiki/SHA-2)
- [Steganography - Wikipedia](https://en.wikipedia.org/wiki/Steganography)

---

## 👤 Author

**Debanga Guria**  
B.Tech CSE – AI & ML  
Brainware University  

---

> 📬 Feel free to use and modify this project for learning or research purposes.
