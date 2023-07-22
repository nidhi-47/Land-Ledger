# Land Ledger - Decentralized Land Management System

Land Ledger is a revolutionary decentralized land management system that leverages Blockchain technology to address the longstanding problem of disputes in land ownership. By implementing a blockchain network using Proof-of-Stake (PoS) and cryptographic techniques like Merkle trees consensus, Land Ledger ensures the immutability, integrity, and transparency of land ownership records.

## Features

- Decentralized land management system utilizing Blockchain technology.
- Proof-of-Stake (PoS) consensus mechanism for secure and efficient transaction validation.
- Merkle trees consensus for cryptographic integrity and data verification.
- Transparent and immutable land ownership records to prevent disputes.
- RESTful API developed with the Flask framework in Python for easy access to land ownership records.

## Installation

Follow the steps below to set up Land Ledger on your system:

1. Clone the Land Ledger repository:
    ```
    git clone https://github.com/YashVardhanSingh01/Land-Ledger.git
    cd Land-Ledger
    ```
2. Install the required dependencies:
    ```bash
   pip install -r requirements.txt
    ```

## Getting Started

1. Start the Land Ledger blockchain network and the RESTful API by:
    ```bash
   python3 PoS.py
    ```
3. Use Postman Application to Test Endpoints
    * Install Postman if you haven't already.
    * Open Postman and use http://localhost:5000 as the url.
    * Use the different endpoints to access land ownership records and verify the functionality of the system.

## Land Ledger API Example Requests and Responses

### Example API Request and Response for `/add-user`:

#### Python Request:
```python
import requests

url = 'http://localhost:5000/add-user'
user_data = {
    'user_id': 123,
    'user_wallet': '0x4F3D5D6C9A1B2E8A',
    'list_of_pid': [1, 2, 3]
}

response = requests.post(url, json=user_data)
print(response.json())
```
#### JSON Response:
```json
{
    "uid": 123,
    "ustake": 0,
    "uwallet": "0x4F3D5D6C9A1B2E8A",
    "prop_list": [1, 2, 3]
}
```
### Example API Request and Response for `/add-property`:

#### Python Request:
```python
import requests

url = 'http://localhost:5000/add-property'
property_data = {
    'property_id': 1,
    'price': 100000,
    'owner': 'John Doe'
}

response = requests.post(url, json=property_data)
print(response.json())
```
#### JSON Response:
```json
{
    "pid": 1,
    "price": 100000,
    "owner": "John Doe"
}
```
### Example API Request and Response for `/add-transaction`:

#### Python Request:
```python
import requests

url = 'http://localhost:5000/add-transaction'
transaction_data = {
    'pid': 1,
    'buyer': 'Alice',
    'seller': 'Bob'
}

response = requests.post(url, json=transaction_data)
print(response.json())
```
#### JSON Response:
```json
{
    "buyer": "Alice",
    "seller": "Bob",
    "pid": 1,
    "validation_status": "Valid"
}
```
### Example API Request and Response for `/add-block`:

#### Python Request:
```python
import requests

url = 'http://localhost:5000/add-block'
block_data = {
    'merkle_root': '0x3B67F11C5A9D2C6A',
    'validator': 'Validator1'
}

response = requests.post(url, json=block_data)
print(response.json())
```
#### JSON Response:
```json
{
    "block_hash": "0x1F7E84D6A18B6E90"
}
```
### Example API Request and Response for `/validate-chain`:

#### Python Request:
```python
import requests

url = 'http://localhost:5000/validate-chain'

response = requests.get(url)
print(response.json())
```
#### JSON Response:
###### Response (Valid Chain):
```json
{
    "message": "Blockchain is valid"
}
```
###### Response (Tampered Chain):
```json
{
    "message": "Blockchain has been tampered with"
}
```
### Example API Request and Response for `/view-history/<int:number>`:

#### Python Request:
```python
import requests

url = 'http://localhost:5000/view-history/1'

response = requests.get(url)
print(response.json())
```
#### JSON Response:
```json
{
    "property_id": 1,
    "transaction_history": [
        {
            "buyer": "Alice",
            "seller": "Bob",
            "timestamp": "2023-07-25 12:45:00"
        },
        {
            "buyer": "Charlie",
            "seller": "Alice",
            "timestamp": "2023-07-26 10:20:00"
        }
    ]
}
```
### Example API Request and Response for `/tamper/<int:number>`:

### Python Request:
```python
import requests

url = 'http://localhost:5000/tamper/2'

response = requests.get(url)
print(response.json())
```
#### JSON Response:
```json
{
    "tampered_blockchain": [
        {
            "index": 1,
            "previous_hash": "0F3C2E1A86B4DF5E",
            "timestamp": "2023-07-24 18:30:00",
            "Merkle_root": "hacked",
            "validator": "Validator1",
            "hash": "13AFC0E3D37B9A7D"
        },
        {
            "index": 2,
            "previous_hash": "13AFC0E3D37B9A7D",
            "timestamp": "2023-07-25 08:15:00",
            "Merkle_root": "3B67F11C5A9D2C6A",
            "validator": "Validator2",
            "hash": "1F7E84D6A18B6E90"
        }
    ]
}
```
Please note that these are example requests and responses, and the actual data may differ based on your implementation and data input.

## Contributions

Contributions to enhance the Land Ledger decentralized land management system are welcome. If you have suggestions for improvements or encounter any issues, feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License.
