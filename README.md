ITIS6200-Course-Project


Project Title: Hash-based Blockchain Implementation


Overview:

This project implements a simplified blockchain system using Python and Flask to demonstrate core concepts such as block creation, hashing, proof-of-work mining, transaction handling, and decentralized consensus. Multiple nodes communicate via REST APIs, simulating a peer-to-peer network where each node maintains its own copy of the blockchain. Nodes can connect, add transactions, mine blocks, and use the longest-chain rule to achieve consensus across the network. This implementation serves as a hands-on educational model that showcases how real-world blockchain systems operate in a secure, transparent, and decentralized manner.


Project Structure:

├── ITIS 6200 Course Project            # Parent Folder / Directory

  ├── Node01.py            # This python file represents one decentralized node (Node01) in the network

  ├── Node02.py            # This file represents Node02 in the decentralized network
  
  ├── Node03.py            # This file represents Node03 in the decentralized network
  
  ├── nodes.json           # List of blockchain nodes
  
  ├── transaction.json     # Example transaction structure
  
  ├── README.md            # Detailed project documentation 


System Arichecture:

<img width="884" height="842" alt="image" src="https://github.com/user-attachments/assets/3dde6069-ae27-4a21-84e9-d8b53924c707" />


Approach:

1. Implement a Blockchain class with all core methods

2. Create REST API endpoints using Flask

3. Run multiple nodes on different ports to simulate decentralization

4. Use Postman for testing GET/POST requests

5. Use JSON files for node connections and transactions

The execution flow followed this sequence:

Connecting nodes → Transaction → Mining → Validation → Consensus

Software Used:

Spyder IDE from Anaconda Distribution: https://www.anaconda.com/download

Postman HTTP Client: https://www.getpostman.com/

Flask: Web framework for API


Installation and Setup:

Clone the repository: git clone https://github.com/janetchristina/ITIS6200-Course-Project.git

Flask: pip install Flask

requests: pip install requests


Challenges during implementation:

1.	Running nodes on the same port 5000.

2.	Nodes became inconsistent when blocks were mined separately.

3.	Transactions didn’t appear immediately in the chain.


Mitigations:

1.	Switched to running nodes on individual ports (5001, 5002, 5003).

2.	Implemented longest-chain consensus via /replace_chain.

3.	Transactions included in the next mined block; triggered /mine_block after adding.


How to run:

The three Python files represent three nodes with ports 5001, 5002, and 5003, respectively. Run three of these files in three different terminals. This line of code, app.run(host='0.0.0.0', port=5001) is used to run the app. 

Each node is running on a designated port:

Node01 on port 5001

Node02 on port 5002

Node03 on port 5003

To interact with the Blockchain, we need to open Postman and open three tabs for these three nodes as well. We make some GET and POST requests to play with the blockchain’s functionality.

GET Requests:

1.	http://127.0.0.1:5001/get_chain

    Returns the full blockchain along with its current length.

2.	http://127.0.0.1:5001/mine_block

    Mine a new block using Proof of Work, and add it to the blockchain, and add/welcome the new transaction to a new block 

3.	http://127.0.0.1:5001/is_valid

    Validates the blockchain to check if all blocks follow consensus and are compliant with the defined rules

5.	http://127.0.0.1:5001/replace_chain 

    This is used to bring all blocks in the decentralized network to consensus.

Note: The port numbers have to be changed based on the node in use. 


POST Requests:

1. http://127.0.0.1/connect_node

Used to connect multiple nodes and form a decentralized peer-to-peer network.

Node01:

{  	

    "nodes": ["http://127.0.0.1:5002",
   
              "http://127.0.0.1:5003"]

}

Node02:

{

    "nodes": ["http://127.0.0.1:5001",

              "http://127.0.0.1:5003"]

}

Node03:

{
 
  "nodes": ["http://127.0.0.1:5001",

            "http://127.0.0.1:5002"]

}


3. http://127.0.0.1/add_transaction

Adds a transaction to the mempool, which will be included in the next mined block.

Note: The JSON files should be put in the Body > raw > select JSON format

Example:

Node_01

{

    "sender": "Bob",
    
    "receiver": "Alice",
    
    "amount": 100

}


Conclusion:

This project implements a functional blockchain with mining, transactions, and node synchronization. It addresses real-world challenges like chain consistency, modular code, and API handling. The project provides a solid foundation for learning and extending blockchain concepts.
