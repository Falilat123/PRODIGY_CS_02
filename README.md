# Image Encryption Tool

This project is a simple image encryption and decryption tool that uses pixel manipulation techniques such as XOR operations and mathematical transformations on pixel values. It allows users to encrypt and decrypt images with a user-provided integer key.

## Features

- **Encrypt Image:** Encrypts an image by performing XOR and addition operations on each pixel.
- **Decrypt Image:** Reverses the encryption process, restoring the original image.
- Supports `.jpg`, `.jpeg`, and `.png` image files.
- A simple GUI is provided using `Tkinter`.

## Prerequisites

Before you run this script, you need to have Python installed. The project also relies on the following libraries, which come by default with Python:
- `tkinter`
- `os`

## How It Works

- **Encryption:**
  - The tool uses a user-provided integer key to XOR each pixel value.
  - After XOR, it adds a constant value (5) to each pixel and wraps the result around at 256.
  - The encrypted image is saved as `encrypted_image.png` in the same directory as the script.

- **Decryption:**
  - To decrypt, the tool subtracts 5 from each pixel value and then XORs it with the user-provided key.
  - The decrypted image is saved as `decrypted_image.png` in the same directory.

## How to Use

1. Clone or download the project.
2. Run the script using Python:

    ```bash
    python image_encryption_tool.py
    ```

3. The application window will appear:
   - Click **Encrypt Image** to select an image, enter the key, and encrypt the image.
   - Click **Decrypt Image** to select an encrypted image, enter the key, and decrypt the image.

## Code Explanation

```python
from tkinter import *
from tkinter import filedialog, messagebox
import os
```
- The script uses `Tkinter` for the graphical interface and os for file handling.

## Encryption Function
```python
def encrypt_image():
    file_path = filedialog.askopenfilename(filetypes=[("Image files", ".jpg;.jpeg;*.png")])
    ...
    key = int(entry1.get(1.0, END).strip())  # Get the key from the user
    ...
    for index, value in enumerate(image):
        image[index] = value ^ key  # XOR with key
        image[index] = (image[index] + 5) % 256  # Add 5 to each pixel value
    ...
    with open(new_file_path, "wb") as file:
        file.write(image)

## Decryption Function
```python
def decrypt_image():
    file_path = filedialog.askopenfilename(filetypes=[("Image files", ".jpg;.jpeg;*.png")])
    ...
    key = int(entry1.get(1.0, END).strip())  # Get the key from the user
    ...
    for index, value in enumerate(image):
        image[index] = (value - 5) % 256  # Subtract 5 from each pixel value
        image[index] = image[index] ^ key  # XOR with key
    ...
    with open(new_file_path, "wb") as file:
        file.write(image)
```

## GUI Layout
- The GUI provides buttons to encrypt or decrypt an image and a text field to input the encryption key.
```python
b1 = Button(root, text="Encrypt Image", command=encrypt_image, ...)
b2 = Button(root, text="Decrypt Image", command=decrypt_image, ...)
entry1 = Text(root, height=1, width=10, ...)
```

## Customization
- You can modify the pixel manipulation logic to suit different encryption patterns.
- The file names for encrypted and decrypted images can be changed by modifying the new_file_path variable.

## Disclaimer
This tool is intended for educational purposes only. Ensure you have the right to encrypt and decrypt any image you use.