# WhatsApp Backup Google Driver Downloader Decryptor

![PyPI - Version](https://img.shields.io/pypi/v/wabdd?color=green)

## Usage

### Using PyPi

1. Install the `wabdd` package

    ```shell
    pip install wabdd
    ```

2. Get token

    ```shell
    wabdd token YOUR_GOOGLE@EMAIL.ADDRESS
    ```

3. Download backup

    ```shell
    wabdd download --token-file /tokens/YOUR_GOOGLE_EMAIL_ADDRESS_token.txt
    ```

4. Decrypt backup

    ```shell
    wabdd decrypt --key-file keys/PHONE_NUMBER_decryption.key dump backups/PHONE_NUMBER_DATE
    ```

### Prerequisites (only for poetry and docker)

1. Clone repository

    ```shell
    git clone https://github.com/giacomoferretti/whatsapp-backup-downloader-decryptor
    ```

2. Write down your backup decryption key
   - RECOMMENDED: create a folder named `keys` and store your key there

### Using Poetry

1. Install dependencies

    ```shell
    poetry install
    ```

2. Get token

    ```shell
    poetry run wabdd token YOUR_GOOGLE@EMAIL.ADDRESS
    ```

3. Download backup

    ```shell
    poetry run wabdd download --token-file /tokens/YOUR_GOOGLE_EMAIL_ADDRESS_token.txt
    ```

4. Decrypt backup

    ```shell
    poetry run wabdd decrypt --key-file keys/PHONE_NUMBER_decryption.key dump backups/PHONE_NUMBER_DATE
    ```

### Using Docker

1. Build docker image

    ```shell
    docker build . -t wabdd:0.1.2
    ```

2. Get token

    ```shell
    docker run -it --rm --user $(id -u):$(id -g) -v $(pwd)/tokens:/tokens wabdd:0.1.2 token YOUR_GOOGLE@EMAIL.ADDRESS
    ```

3. Download backup

    ```shell
    docker run -it --rm --user $(id -u):$(id -g) -v $(pwd)/backups:/backups -v $(pwd)/tokens:/tokens wabdd:0.1.2 download --token-file /tokens/YOUR_GOOGLE_EMAIL_ADDRESS_token.txt
    ```

4. Decrypt backup

    ```shell
    docker run -it --rm --user $(id -u):$(id -g) -v $(pwd)/backups:/backups -v $(pwd)/keys:/keys wabdd:0.1.2 decrypt --key-file keys/PHONE_NUMBER_decryption.key dump backups/PHONE_NUMBER_DATE
    ```
