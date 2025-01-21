# Encryption-Python-Project

This project is a simple web application for encrypting and decrypting files using AES encryption in CBC mode. The application is built with Flask and uses the PyCryptodome library for cryptographic operations.

## Features

- Encrypt files using AES encryption in CBC mode.
- Decrypt files that were encrypted by the application.
- HMAC verification to ensure file integrity.

## Requirements

- Python 3.x
- Flask
- PyCryptodome

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/Encryption-Python-Project.git
    cd Encryption-Python-Project
    ```

2. Create a virtual environment and activate it:
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install the required packages:
    ```sh
    pip install -r requirements.txt
    ```

## Usage

1. Run the Flask application:
    ```sh
    python app.py
    ```

2. Open your web browser and go to `http://127.0.0.1:5000`.

3. Use the web interface to upload a file and provide a passphrase for encryption or decryption.

## Project Structure

- `app.py`: The main Flask application file containing routes and encryption/decryption logic.
- `templates/index.html`: The HTML template for the web interface.
- `uploads/`: Directory where uploaded files are stored temporarily.

## Functions

### `generate_key(passphrase: str, salt: bytes) -> bytes`
Generates a 256-bit key from a passphrase and salt using PBKDF2 with SHA256.

### `encrypt_file(file_path: str, key: bytes)`
Encrypts a file using AES in CBC mode. It generates a random IV, pads the plaintext, and computes an HMAC for integrity verification. The encrypted file is saved with a `.enc` extension.

### `decrypt_file(file_path: str, key: bytes)`
Decrypts a file that was encrypted by the application. It verifies the HMAC to ensure the file's integrity, removes the padding, and saves the decrypted file.

### `index()`
Renders the main page of the web application.

### `encrypt()`
Handles the file upload and encryption process. It saves the uploaded file, encrypts it, and sends the encrypted file back to the user.

### `decrypt()`
Handles the file upload and decryption process. It saves the uploaded file, decrypts it, and sends the decrypted file back to the user. If HMAC verification fails, it returns an error message.

## Security Notes

- The passphrase is used to derive a 256-bit key using PBKDF2 with a fixed salt. For better security, consider using a unique salt for each encryption operation.
- The application uses HMAC to verify the integrity of the encrypted files. If the HMAC verification fails during decryption, the file may be corrupted or tampered with.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## GitHub Tags

- `encryption`
- `AES`
- `Flask`
- `Python`
- `file-encryption`
- `web-application`
- `HMAC`
- `PyCryptodome`
