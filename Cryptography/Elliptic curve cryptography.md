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

3. Kryptografie eliptických křivek
- Eliptické křivky jsou speciálním typem kubických křivek.
- Eliptické křivka nemá nic společného s elipsou. Důvod je jen, že kubická funkce má tvar elipsy.
- ECC je založena na dvou algebraických strukturách: Konečné těleso F a eliptická křivka E.
- Kryptografické klíče v ECC jsou podstatně kratší.

4. Bezpečnostní úrovně - NIST
- Bezpečnost ECC je založena na problému diskrétního logaritmu nad eliptickou křivkou (ECDL)
- ECDL je rychlý, ale ještě pomalejší než klasický DL problém

5. ECDL a DL problém
- ECDL (Elliptic Curve Discrete Logarithm): Je DL problém nad množinou bodů eliptické křivky nad konečným tělesem
![[Pasted image 20231226150911.png]]
![[Pasted image 20231226203513.png]]
- This is the function in the simplified Weierstrass form
![[Pasted image 20231226203754.png]]

6. Smooth elliptic curve
- The curve is smooth if it does not contain singularity point (weird point, there is 0 or many tangent). For the regular point, there is only 1 tangent.
- To form a group over the object F, the curve needs to be smooth
	- Elliptic curve group is additive (+)
- Singularity point: 
![[Pasted image 20231226211240.png]]
- Finite object:
![[Pasted image 20231226211427.png]]
- Order of elliptic curve
![[Pasted image 20231226213904.png]]
![[Pasted image 20231226215106.png]]
![[Pasted image 20231226232253.png]]

7. Sčítání bodů
![[Pasted image 20231227083232.png]]
![[Pasted image 20231227083326.png]]
![[Pasted image 20231227083405.png]]
![[Pasted image 20231227083434.png]]

8. Skalární násobení bodu
![[Pasted image 20231227084206.png]]
![[Pasted image 20231227084805.png]]

9. Problém diskrétního logaritmu nad eliptickou křivkou
- Je založen na složitosti efektivního počítání bodů eliptické křivky nad konečným tělesem
![[Pasted image 20231227085143.png]]
![[Pasted image 20231227085322.png]]

10. Bilineární párování
- Další vlastnost nebo operace (není v ECC, ale může být používán s kombinací ECC)
![[Pasted image 20231228133147.png]]
![[Pasted image 20231227100016.png]]
![[Pasted image 20231227100037.png]]
![[Pasted image 20231227100236.png]]
![[Pasted image 20231228135443.png]]
- Stupeň křivky
![[Pasted image 20231228141722.png]]

- Problém inverze párování
![[Pasted image 20231228142448.png]]
![[Pasted image 20231228142543.png]]

With the use of pairing, we can create new signatures: Group signatures, ring signatures
- Encryption: Identity-based encryption, attribute-based encryption
![[Pasted image 20231228142600.png]]
![[Pasted image 20231228142744.png]]

11. MOV útok
- Why does modern cryptography prefer the discrete log problem over the additive group of points on an Elliptic Curve defined over a Finite Field rather than integer factorization or the discrete log problem over the multiplicative group of a Finite Field?
![[Pasted image 20231228150828.png]]
- The MOV (Menezes-Okamoto-Vanstone) attack transforms a Discrete Log problem in an Elliptic Curve Group into a Discrete Log Problem in the Multiplicative Group of a Finite Field - i.e. ECDLP to DLP
- Roots of Unity
![[Pasted image 20231228152500.png]]
- Embedding Degree
![[Pasted image 20231228152517.png]]
![[Pasted image 20231228152736.png]]
![[Pasted image 20231228154306.png]]
![[Pasted image 20231228154317.png]]

