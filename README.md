# Jenkins Decryptor

A Python tool to decrypt passwords and private keys stored in Jenkins credentials configuration files (`credentials.xml` or individual job configurations). 

It extracts and decrypts credentials using Jenkins' internal master key (`master.key`) and the secret key (`hudson.util.Secret`).

Originally written by [Thiébaud Weksteen](https://github.com/tweksteen), I modified the code to make it work with Python version 3.12+ as the Pycrypto library is lo longer maintained anymore.

## Prerequisites

- Python 3.12+
- `pycryptodome` library

## Installation

1. Clone this repository.
   ```bash
   git clone https://github.com/wand3rlust/jenkins-decrypt.git
   ```
2. Set up a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

To decrypt credentials, run the `decrypt.py` script by providing the paths to:
1. `master.key` (usually found in `$JENKINS_HOME/secrets/master.key`)
2. `hudson.util.Secret` (usually found in `$JENKINS_HOME/secrets/hudson.util.Secret`)
3. `credentials.xml` (usually found in `$JENKINS_HOME/credentials.xml` or configuration files containing `<password>` or `<privateKey>` blocks)

```bash
python3 decrypt.py <path/to/master.key> <path/to/hudson.util.Secret> <path/to/credentials.xml>
```

### Example

```bash
python3 decrypt.py secrets/master.key secrets/hudson.util.Secret credentials.xml
```
