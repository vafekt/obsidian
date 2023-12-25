1. Reminding about group and object
- Group (G, o) is a kind of set with only one binary operation (o) at the set G. It has the following attributes:
	- Closure: For all elements in the set G (for example, a and b), with structure under * (multiply), a * b also belongs to the set G
	- Associativity: For a, b, c belongs to G, a * (b * c) = (a * b) * c
	- Identity element (neutral element): there exists element e (also in G) such that for all other elements (a in G), we have e o a = a and a o e = a
	- Inverse: there exists a' in G (called inverse of a) such that a o a' = e, and a' o a = e
- Order of a group: The number of elements of a group (finite or infinite) is called its order. We will use |G| to denote the order of G.
- Order of an element: The order of an element g in a group G is the smallest positive integer n such that g^n = e (in additive notation, ng = e). If no such integer exists, we say that g has infinite order. The order of an element g is denoted by |g|.
- Subgroups: A subgroup of a group (G, ◦) is a group (H, ⋄) such that H ⊆ G and for all a, b ∈ H, we have that a ⋄ b = a ◦ b. If (H, ⋄) is a subgroup of (G, ◦), we write (H, ⋄) ≤ (G, ◦).
	- (Z, +) ≤ (Q, +) ≤ (R, +) ≤ (C, +).
- Cyclic group: A group G is cyclic if G = [a]  = {a^n | n ∈ Z}. The element, a, which generates G is called a generator of G and need not be unique.
	- Every group is Abelian (commutative a ◦ b = b ◦ a)
![[Pasted image 20231225091003.png]]
![[Pasted image 20231225100907.png]]
![[Pasted image 20231225101015.png]]
2. Popular problem in cryptography
- Factorization: Depends on factorization of large number
	- Dividing the large number into the product of prime numbers
	- Example: RSA
	![[Pasted image 20231225102336.png]]
	![[Pasted image 20231225111111.png]]
	- Problem is from the large number n, which is comprised from p and q. 
	- In [cryptography](https://en.wikipedia.org/wiki/Cryptography "Cryptography"), the **strong [RSA](https://en.wikipedia.org/wiki/RSA_(algorithm) "RSA (algorithm)") assumption** states that the [RSA problem](https://en.wikipedia.org/wiki/RSA_problem "RSA problem") is intractable even when the solver is allowed to choose the public exponent _e_ (for _e_ ≥ 3). More specifically, given a modulus _N_ of unknown factorization, and a ciphertext _C_, it is infeasible to find any pair (_M_, _e_) such that _C_ ≡ _M_ _e_ mod _N_.
- Problem of discrete logarithm
	- The discrete logarithm problem is another fundamental concept in the field of cryptography, particularly in the context of public-key cryptosystems based on certain mathematical structures. The problem involves finding the exponent x in the equation g^x ≡ ℎ(mod p), where g, h, and p are known values. In other words, given a base g, a modulus p, and the result h, the goal is to find the exponent x.
	- Here's a breakdown of the terms:
		- g: The generator of a cyclic group modulo p. 
		- h: The result of raising g to the power of x and taking the remainder when divided by p.
		- p: A large prime number.
	- It is used in DSA. DSA is primarily designed for digital signatures. Digital signatures are used to verify the authenticity and integrity of digital messages or documents. In DSA, a private key is used to generate a digital signature, and a corresponding public key is used to verify the signature. But RSA is used for both encryption and digital signatures.
	- x is the private key and h is the public key.
	![[Pasted image 20231225112655.png]]
- Problem of Diffie Hellman
![[Pasted image 20231225113319.png]]
![[Pasted image 20231225113409.png]]
3. 