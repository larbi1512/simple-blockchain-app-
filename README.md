# Simplified Blockchain in Python with Flask

This repository contains a lab project that demonstrates the foundational principles of blockchain technology. we built a simplified blockchain from scratch using Python. we implemented core blockchain functionalities such as block creation, mining (proof-of-work), chaining, and validation. Finally, we deploy our blockchain as a basic web application using Flask.

## Overview

The project includes:
- **Blockchain Class**: Implements block creation, mining using a proof-of-work algorithm, and chain validation.
- **Flask Web Application**: Provides REST endpoints to mine new blocks, retrieve the blockchain, and check its validity.
- **Core Concepts**: Learn how blocks are chained together using cryptographic hashes, how mining secures the chain, and how consensus is achieved.

## REST API Endpoints

The Flask application provides three main endpoints:

- **Mine a New Block**  
  **Endpoint:** `/mine_block`  
  **Method:** GET  
  **Description:** Mines a new block by performing the proof-of-work algorithm, adds it to the blockchain, and returns block details.  
  **Example Response:**
  ```json
  {
      "message": "Congratulations, you just mined a block!",
      "index": 2,
      "timestamp": "2025-02-20 14:35:00.123456",
      "transactions": [],
      "proof": 35293,
      "previous_hash": "a3f5b7c..."
  }
  ```

- **Get the Blockchain**  
  **Endpoint:** `/get_chain`  
  **Method:** GET  
  **Description:** Retrieves the full blockchain and its length.  
  **Example Response:**
  ```json
  {
      "chain": [
          { "index": 1, "timestamp": "2025-02-20 14:30:00.000000", ... },
          { "index": 2, "timestamp": "2025-02-20 14:35:00.123456", ... }
      ],
      "length": 2
  }
  ```

- **Validate the Blockchain**  
  **Endpoint:** `/is_valid`  
  **Method:** GET  
  **Description:** Checks whether the blockchain is valid (i.e., no tampering has occurred) and returns a boolean status.  
  **Example Response:**
  ```json
  {
      "is_valid": true
  }
  ```

## Code Explanation

- **Blockchain Class:**
  - **Initialization:**  
    Creates the genesis block (first block) and initializes the chain and transactions list.
  - **create_block:**  
    Generates a new block with a timestamp, proof (result of mining), and the previous block’s hash.
  - **proof_of_work:**  
    Implements a simple proof-of-work algorithm. It searches for a number (proof) such that the hash of the operation (new_proof² - previous_proof²) starts with a specified number of zeros (determined by the `difficulty` parameter).
  - **hash:**  
    Returns the SHA-256 hash of a given block.
  - **chain_valid:**  
    Iterates through the chain to verify that each block’s `previous_hash` correctly links to the hash of the previous block and that the proof-of-work is valid.

- **Flask Endpoints:**  
  The endpoints interact with the blockchain instance, allowing users to mine blocks, retrieve the chain, and validate its integrity through HTTP requests.


## License

This project is open source and available under the [MIT License](LICENSE).
