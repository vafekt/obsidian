1. Commitment scheme
![[Pasted image 20231229211807.png]]
![[Pasted image 20231229204527.png]]
![[Pasted image 20231229212147.png]]
A commitment scheme is a two-phase protocol between a Sender and a Receiver
- The Sender holds a message m and, in the first phase, it picks a random key K and then “encodes” the message using the key and sends the encoding (a commitment to m) to the Receiver
- The Receiver can open the commitment and find out the content of the message m.
Two security properties
- Hiding: Receiving a commitment to a message m should give no information to the Receiver about m.
- Binding: The Sender cannot “cheat” in the second phase and send a different key K' that causes the commitment to open to a different message m'.
A commitment scheme allows one to commit to a message without revealing it.
![[Pasted image 20231230110256.png]]
![[Pasted image 20231230110422.png]]
![[Pasted image 20231230110526.png]]
Commitment schemes are used in zero-knowledge proof protocols. In a zero-knowledge proof, one party (the prover) can convince another party (the verifier) that a statement is true without revealing any information about the statement itself. Commitment schemes are often employed to commit to certain values in the course of these proofs.

2. Attributes
![[Pasted image 20231230132102.png]]
![[Pasted image 20231230132145.png]]

3. Levels of commitment








