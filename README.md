# Boolean-Coin
This repository was created for a University programming project on the topic of blockchains.

Programming Project 10: Blockchain
Manual



Noah Mamié (17-607-714)
Neel Nathan (17-602-210)
Ruhika Singh (17-613-381)
Lars Egger (17-603-903)
Nga Hangi Lin (18-600-999)
Simon Schmidlin (17-604-489)

Programming: Introduction Level
HS18 - 3,793,1.00
December 21, 2018

Mario Silic
The Booleans
Python


Introduction
"You can't stop things like Bitcoin. It will be everywhere, and the world will have to readjust. World governments will have to readjust", John McAfee commented on the latest developments in the FinTech industry (Marr, 2018). As a result of promising predictions for Bitcoin alike the one from John McAfee, we were eager to understand the fundamentals behind it. Despite the cryptocurrency hype towards the end of 2017, we found ourselves rather interested in how the transactions of these technologies work, namely Blockchain technology. Enhanced security, improved traceability and reduced costs are only a few of the reasons why blockchain technologies hold huge potential to disrupt any type of industry (Hooper, 2018).
Having realized the importance of blockchain technologies, we intend to acquire the necessary skills and knowledge about the composition and functioning of blockchains. In a second step, the primary objective of this project is to compute our own individual blockchain. Finally, we aim at implementing a transaction validation mechanism into our blockchain in order to enable our code to be used as an actual cryptocurrency. 
In order to provide insight into our code and the work process behind it, this manual continues with a short input about theoretical characteristics of blockchain technology. Subsequently, our approach is elaborated, which includes applied procedural methods, outcomes and obstacles on our way. 
Lastly, it is important to mention that our project is written in Python. We have chosen to focus on a Python project due to the simplicity and wide use of the language, given most of us were new to coding.
Blockchain in theory
This part of the manual focuses on the fundamentals of blockchain structures. The aim is to explain  how a blockchain works and is constructed in plain English, so that the code may be easier to follow. 
First of all, a blockchain is an immutable, sequential chain. It consists of so called blocks that are chained together through hashes. Any individual block is able to store any kind of data. In the case of cryptocurrencies, blocks are utilized for the storage of transactions (van Flymen, 2017). 
As mentioned, hashes connect individual blocks to form a chain. Basically, hashing means taking an input string of any length and giving out an output of a fixed length. When talking about cryptocurrencies the input is defined by occurring transactions. The necessity of hashing becomes clear when dealing with large amounts of data. Instead of remembering the large input data, one can simply keep the hash of a fixed length in mind (Blockgeeks Inc, n.d.).
Now, what does a single block compose of? Each block consists of an index, a timestamp, a list of transactions (in the case of cryptocurrencies), a proof and the hash of the previous block. The hash of the previous block connects the new block to the whole chain and by that creates immutability.  The index serves as an internal reference point while the timestamp is needed to simply store the date and time of a block and its transactions (van Flymen, 2017).
The proof algorithm of each block is referred to as Proof of Work (PoW). It is needed to add new blocks to the chain (mining). The goal of the Proof of Work is to find a solution to a mathematical problem. If the the problem is solved, a new block is created and added to the blockchain  (van Flymen, 2017).
To conclude, a blockchain consists of individual blocks with the same structure. When composing a blockchain, a blueprint for such blocks is constructed, that consists of all necessary elements that have been discussed above.

Our Approach
This chapter specifies how we approached the project, gives insight into our work process and focuses on obstacles we faced.

First of all, we mainly followed the manual of Nash (2017), when constructing our blockchain. It helped us to get a clear idea of the required steps and provided us with a basis for our blockchain. After getting an idea and understanding the blockchain of Nash (2017), we started working on ours by making specifications and adaptations. Moreover, we commented every single step of our code to make it understandable for third parties. 

The blockchain commences by importing databases like datetime or hashlib which we require for the composing the code. In a second step, the structure of one block (“Boolean Coin Block”)  is specified. 
In implementing the blocks, we utilized the constructors for hash algorithms, sha 256( ) which returns the hash object with a simple interface with a fixed 256-bits length. Some constant attributes of the hash objects are also included, for instance the hash.hexdigest( ) where the digest of strings is returned as a string of double length, containing only hexadecimal digits. (PSF, 2018) 

Having defined the structure of a general block, the blockchain blueprint continues with the manual creation of a genesis block (first block of the chain). The details of the genesis block can be gathered from our comments in the code. However, it is important to note that the Proof of Work in the genesis block must be seven, as this is the length of the word “Boolean”. After having created the first block, the next step in our code automatically creates and adds new blocks to the chain, which is a process referred to as “mining”. These blocks include general data, such as index, timestamp and hash, always in relation to the previous block. Further, the proof of work of each block has to be a multiple of seven and divisible by the proof of work of the previous block.

Finally, the last part of our code has the function of transforming our blockchain into a decentralized server, that enables us to form a network for the Boolean Coin (@node.route). Furthermore, this network automatically keeps each note updated, as it is important that every user’s blockchain is identical to the longest one. After running the full Boolean Coin server code, the following commands need to be run in the terminal (cURL needs to be installed):

1. Create a transaction.
curl "localhost:5000/txion" \
     -H "Content-Type: application/json" \
     -d '{"from": "akjflw", "to":"fjlakdj", "amount": 3}'

2. Mine a new block.
curl localhost:5000/mine
