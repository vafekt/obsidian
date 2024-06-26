1. Úvod do bezpečnosti vestavěných (embedded) systémů a odolných zařízení
- Základní pojmy a terminologie
	- Autentizace: proces ověření ID určité entity (člověk, stroj, proces)
	- Autorizace: proces získávání souhlasu s provedením nějaké operace
	- Kontrola přístupu: proces povolení nebo odepření k použití určitého zdroje (místo, materiál, data)
	- Tamper-resistant: odolnost vůči manipulaci/narušení nějakého zařízení / součásti / čipu za účelem získání dat
	- Tamper-evident: detekce pokusu o neautorizovaný přístup tj. manipulaci / narušení (slabší vlastnost než tamper-resistant)
	- ISO 7498-2 poskytuje architekturu pro bezpečnost v Open System. Služby:
		- Autentizace. 
		- Řízení přístupu. 
		- Důvěrnost– utajení dat před neautorizovanými entitami, např. šifrování AES. 
		- Nepopiratelnost- ochrana proti odmítnutí původu zprávy (non-repudiation), např. digitální podpis RSA. 
		- Integrita- neměnnost dat během přenosu či ukládání, např. HMAC
	- Kryptosystémy
		- Symetrické kryptosystémy
			- Blokové šifry – AES, TDES, Camellia, Blowfish,… 
			- Proudové šifry – ChaCha, Salsa,… 
			- Autentizační kódy – HMAC, CMAC
		- Asymetrické kryptosystémy
			- Šifrování – RSA, ElGamal,… 
			- Digitální podpis – RSA, ECDSA, EdDSA, DSA,… 
			- Ustanovení klíče – ECDH, DH
		- Další kryptografické funkce
			- Generátory náhodných čísel – PRNG, TRNG,… 
			- Hashfunkce – SHA-2, SHA-3, Whirpool,… 
			- KeyDerivation Funkce – PBKDF2 (RFC 2898) založena na SHA-2
	- Počítačová bezpečnost (kyberbezpečnost): udržování správných vlastností a služeb na počítačových systémech i v případě inteligentních útočníků (podoblasti SW bezpečnost, HW bezpečnost, síťová bezpečnost, sociální inženýrství)
		- Hardwarová bezpečnost zabývá se chybami a útoky v hardwarové části počítačových systémů a možností ochran a detekcí útoků.
		- Softwarová bezpečnost – oblast zabývající se jak útočník může využít/zneužít software a jak se bránit
		- Síťová bezpečnost – zabývá se chybami a zranitelnostmi síťových protokolů, služeb a zařízení a navrhuje možná protiopatření, ochrany a detekce.
	- Trusted Platform Module (TPM)
		- dedikovaný mikrokontrolér, který ukládá klíče a provádí kryptografické operace (šifrování, podpis, hash, …)
		- Located in motherboard of PC
		- provides secure storage that is exceptionally difficult to break because it is a separate component independent of the device’s operating system. So it is not vulnerable to any security risk in the OS itself or any software-based attacks. It is not vulnerable to physical attacks either; the TPM chip can tell if the hardware has been tampered with or removed and can be configured into a self-destruct mode against attacks.
		- According to Microsoft, TPM has been shown to reduce malware attacks by 60% on tested devices. With the TPM technology onboard, you can use it to store biometrics data and ditch passwords completely.
	- Kryptoprocesor
		- dedikovaný / pomocný procesor pro vykonání kryptografických funkcí.
	- Secure Access Module (SAM) – založen na SmartCard technologii, jeho úkolem je poskytnout kryptografické funkce (autentizace) a bezpečné uložiště (typicky velikost SIM)
	- Hardware Security Module (HSM) – výpočetní zařízení pro ukládání a správu klíčů pro silnou autentizaci, poskytuje i kryptografické operace.
	- Postranní kanál nežádoucí způsob výměny informace mezi kryptografickým modulem a jeho okolím.
		- Timing, energy, EM sniffing to attack.
		- Ex: Attacking by listening to sound from telephone when tapping numbers
	- Single points of Failure
		- một sai sót hoặc trục trặc trong thiết kế hoặc vận hành có thể dẫn đến sự cố nghiêm trọng của toàn bộ hệ thống và mất mát tài sản sau đó.
			- **Lưu trữ vật lý duy nhất**
			- **Người giám sát tài chính duy nhất**
		- část systémů, která v případě selhání zapříčiní selhaní celého systému nežádoucí pro systémy Fault-tolerant
	- Reverzní inženýrství proces, jehož cílem je odkrýt princip fungování zkoumaného předmětu/kódu.
- Úvod do bezpečnosti vestavěných systémů
	- Definice: snižování zranitelností a zavádění ochran před hrozbami na vestavěných zařízeních a systémech
	- Důležitými požadavky jsou spolehlivost (reliability) a dostupnost služby (availability)
	- Příklady
		- Průmyslové PC
		- Výpočetní jednotky v automatizaci
		- Systemon Chip(SoC)
		- ATM, bankomaty o Multifunkční tiskárny
	- Přístupové systémy (Access Control System)
		- systém, sada komponentů a zařízení se specifickým HW a SW vybavením pro zajištění ochrany přístupu uživatelů ke chráněným prostorům
		- Důležitý prvek: Autentizace
		![[Pasted image 20240420143854.png]]
		- Autentizaci lze kombinovat – vícefaktorová autentizace. 
			- Dvoufaktorováautentizace – např. čip. karta + PIN. 
			- Třífaktorováautentizace – např. čip. karta + PIN + detekce obličeje
2. Lehká kryptografie pro výpočetně a paměťově omezená zařízení
- Metody lehké kryptografie
	- Zařízení mohou být omezená
		- Výpočetně (procesor jen několik MHz)
		- Paměťově (jednotky – desítky KB RAM, EEPROM)
		- V napájecím zdroji– baterie – omezená životnost. 
		- Programově (omezené API v rámci OS, např. u čip. karet)
		- Funkčně–absence např. časovače, TRNG, chybějící periferie
	- Komunikační protokoly mohou být omezené
		- Maximální délka přenášené zprávy. 
		- Maximální přenosová rychlost.
		- Směr komunikace – jednosměrné vysílání / obousměrné vysílaní 
	- Lehká kryptografie
		- kryptografické metody, implementace, schémata, které jsou schopna běžet a zajistit bezpečnost na zařízeních s určitým omezením (lightweight)
		- Nejčastěji se jedná o:
			- Blokové šifry. 
			- Proudové šifry. 
			- Hash funkce.
		![[Pasted image 20240421170106.png]]
		- Metriky pro hardware
			- **GA (Gate Area)**: This metric measures the physical space occupied by logic gates on a chip
			- **GE (Gate Equivalent)**: It represents the number of basic logic gates required to implement the functionality. NAND
			- **LUT (Look-Up Table)**: It stores the output of a digital circuit for all possible input combinations (AND, OR), enabling efficient implementation of Boolean functions.
			- **FF (Flip-Flop)**: a sequential logic circuit element that stores binary information. It captures the state of a digital signal at a particular moment and holds it until the next clock cycle. FFs are essential for implementing memory elements and synchronizing signals in digital systems.
		- Parametry pro lehkou kryptografii
		![[Pasted image 20240421192718.png]]
		- Kompromis ceny, bezpečnosti a výkonu
		![[Pasted image 20240421192755.png]]
		- Máme dvě možnosti pro implementace
			- v SW: flexibilní, jednoduše přenášet a upravovat (jednoduchá změna délky bloků/klíčů atd.) – vhodná u chytrých zařízení s OS
			- v HW: přináší vyšší rychlost a nižší požadavky na velikost kódu,  je často nasazována u senzorů a jiných zařízení, které jsou omezené v napájecím zdroji
- Schémata a implementace lehké kryptografie
	- Blokové šifry
		- Ze klasické šifry (ARE, IDEA) se rozvíjí na lehké verze (mírně upraveno nebo nový)
			- DESL ze DES s 1S-boxem na místo 8
			- Nový: PRESENT (modifikace SPN-substitučně-permutační síti), SIMON (ARX šifry (operace sčítaní, rotace, XoR)), SPECK (ARX šifry (operace sčítaní, rotace, XoR)
		- Parametry
			- Menší délka bloku (typicky 64 – 80 bitů namísto 128 b). 
			- Snížená délka klíče (např. 96 až 128 b). 
			- Snížení náročnosti komponentů a operací (např. redukce počtu S-boxů a jejich velikosti)
			- Implementace pouze nezbytných funkcí
		- 3 hlavní metody vývoje
			- Rozvinutá implementace - Velká paměťová velikost – mnoho zdrojů AREA/GE.
			- Rundová implementace - Redukce počtu AREA/GE – snížení propustnosti.
			- Sériová implementace - Neefektivní v poměru propustnost/zabrané zdroje, dále vyšší složitost.
	- Proudové šifry
		- (ChaCha20, Grain v1, MICKEY 2.0, Trivium)
	- Hash funkce (Keccak, PHOTON, Quark, SPONGENT)
	- MAC funkce (SipHash)
	- Šifry poskytující autentizované šifrování (ACORN, Ascon, AESJAMBU, AES-OTR, CLOC
	- Obecně je asymetrická kryptografie mnohem náročnější z pohledu času i paměti než symetrická kryptografie
		- Přesto existují schémata jako ECC - ECDSA, NTRU
- Výkonnostní testy a metodologie měření kryptografických metod na omezených zařízeních
	- Techniky a metodologie měření
	![[Pasted image 20240421201503.png]]
	![[Pasted image 20240421201635.png]]
	![[Pasted image 20240421201656.png]]
3. Autentizační systémy, technologie a protokoly
- Typy autentizace a autentizační systémy a technologie
	- Authentication refers to the process of verifying someone's (or something's) claimed identity
	- **Knowledge-based Authentication:**
		- Passwords
		- PINs
		- Security Questions, ZKP
	- **Token-based Authentication:**
		- This token acts like a temporary key that verifies your identity for a specific application or API.
		- Mechanisms
			- **User Login:** You provide your username and password to login.
			- **Token Generation:** The server validates your credentials and, if successful, generates a unique token containing encrypted information about your identity and permissions.
			- **Token Exchange:** The server sends the token back to you (usually stored securely or not securely on your device).
			- **Subsequent Requests:** With each subsequent request to the application or API, you send the token instead of your username and password.
			- **Token Validation:** The server receives the token, verifies its authenticity and validity (often with an expiration time), and grants access if everything checks out.
	- **Biometric Authentication**
		- This approach leverages unique physical or behavioral characteristics for verification, such as:
		    - Fingerprint Scanners
		    - Facial Recognition
		    - Iris Scanners
		    - Voice Recognition
		    - Keystroke Dynamics (typing rhythm)
	- **Certificate-based authentication**
		- This method verifies the user’s or machine’s identity by using digital certificates. A digital certificate is an electronic document typically issued by a trusted third-party authority. They contain the user's digital identity, a public key, and the digital signature of the certification authority.
	- **Multi-factor Authentication (MFA)**
		- MFA strengthens security by combining two or more of the categories above. For instance, using a password along with a fingerprint scan for added security.
	- Authentication can be one-way or both ways
- AAA (Authentication, Authorization, and Accounting)
	- **Authentication (Who are you):**
		- This is the initial step where a user's identity is verified. It involves presenting credentials such as:
		    - Username and password combinations
		    - Biometric scans (fingerprint, facial recognition)
		    - Security tokens (hardware keys, software tokens)
		- The chosen method depends on the security level required and user convenience
	- **Authorization (What can you do):**
		- Once identity is confirmed, authorization determines what level of access the user is granted. This could be:
		    - Full access to all resources
		    - Limited access to specific files or applications
		    - Read-only access versus read-write access
		- Authorization is typically based on pre-defined policies associated with user roles or groups.
	- **Accounting (What did you do):**
		- This final stage tracks user activity within the system. It logs information such as:
		    - User login and logout times
		    - Accessed resources (files, applications)
		    - Actions performed (downloads, edits)
		- Accounting data provides valuable insights for:
		    - Security audits and identifying suspicious activity
		    - Resource usage analysis and optimization
		    - User behavior monitoring and compliance checks
	- AAA protocols: Several protocols implement the AAA framework, acting as a communication language between network devices and the central AAA server.
		- **RADIUS (Remote Authentication Dial-In User Service):** A widely adopted protocol for network access control, primarily used for dial-up, VPN, and wireless connections.
		- **Diameter:** A newer protocol designed for next-generation networks, supporting advanced features like mobility and real-time policy enforcement.
	- Root of trust
		- The Root of Trust (RoT) is the foundation for building trust within a security system. It's the initial point from which all other security measures derive their legitimacy.
		- 2 types of RoT implementation
			- **Hardware Security Modules (HSMs):** These are physical devices, often resembling small circuit boards. They are standalone units that can be connected to a server or network.
				- Securely storing and managing cryptographic keys used for encryption and decryption.
				- Performing high-performance cryptographic operations like signing and verifying digital signatures.
				- Used in data centers
			- **Trusted Platform Modules (TPMs):** These are embedded chips within devices like computers, securely storing encryption keys and ensuring platform integrity. You won't see a TPM itself, but it's a crucial component within your device.
				- Securely storing and managing cryptographic keys used for encryption and decryption.
				- Performing high-performance cryptographic operations like signing and verifying digital signatures.
				- Used in personal PCs, laptops
		- RoT vs CA (Certificate Authority)
			- CAs **rely on** an established RoT for their own legitimacy. This could be a pre-programmed key stored in a secure hardware module (HSM) or a trusted boot process on the server issuing certificates.
			- CAs then build a **chain of trust**. The RoT signs the root certificate of the CA, which in turn signs other certificates issued to websites, servers, or individuals. These certificates act as proof of identity in the digital world.
			- CA is entity, RoT is just the initial point
	- Machine authentication
		- Can be authentication of automated human-to-machine or machine-to-machine communication.
		- H2M: přístupový systém, prokázání přístupu ke stroji /OS/ zařízení, PAN
		- M2M: autentizační protokoly v počítačových sítích, WLAN, LAN/MAN,  IoT
	- It can be offline authentication or online authentication
	- Process of authentication (3 basic processes)
	![[Pasted image 20240424000157.png]]
- Scheme of authentication system
![[Pasted image 20240424000430.png]]
- OSDP protocol (Open Supervised Device Protocol)
	- OSDP facilitates communication between a central security management system (like a control panel, terminal) and peripheral devices within an access control system. These peripheral devices include:
		- **Card readers:** Used for swiping access cards or key fobs.
		- **Keypads:** For entering PIN codes for access.
		- **Biometric readers:** For fingerprint, facial recognition, or iris scan verification.
		- **Locks:** Electronic door locks controlled by the system.
	- OSDP supports secure communication with encryption, protecting sensitive data like access codes or user credentials from eavesdropping.
		- Encryption: AES-128 of mode CBC
		- Integrity CRC-16 and MAC
	- OSDP can implement authentication mechanisms to verify the legitimacy of devices communicating with the control panel, preventing unauthorized access attempts.
	- The protocol allows for continuous monitoring of connected devices, detecting potential malfunctions or tampering attempts.
4. Autentizační protokoly a mechanismy pro spoje bod - bod
- PAP protocol (Password Authentication Protocol)
	- Very old protocol, it is not used today in practice, but remains as a historical stone
	- How it works
		- **Client Initiation:** A user attempting to access a network resource (like a server) sends their username and password in plain text (unencrypted) to the authentication server using PAP.
		- **Server Verification:** The server receives the username and password and checks them against a local password database.
		- **Access Granted/Denied:** If the username and password match, the server grants access to the requested resource. Otherwise, access is denied.
		![[Pasted image 20240424131833.png]]
	- Because of plain text transmission and one-factor authentication, it is replaced
- CHAP (Challenge-handshake authentication protocol)
	- Successor of PAP
	- How it works
		- **Client Sends Username:** The user attempting access sends their username to the authentication server.
		- **Server Sends Challenge:** The server generates a random challenge value (like a random number) and sends it to the client.
		- **Client Calculates Response:** The client combines the challenge value with its password (usually a one-way hash) and sends this response back to the server.
		- **Server Verifies Response:** The server performs the same calculation on the received response and the stored password hash. If they match, access is granted. Otherwise, access is denied.
	- Unlike PAP, CHAP doesn't transmit the actual password in plain text. The server only receives a one-way hash of the password combined with the challenge, making it more difficult to crack passwords even if the communication is intercepted.
	- CHAP only provides one-way authentication. The server authenticates the client, but the client doesn't verify the server's legitimacy.
- CHAPv2
	- Update of CHAP
	- Advantages
		- CHAPv2 offers optional mutual authentication. Both the server and the client can challenge each other, providing an additional layer of security.
		- CHAPv2 supports stronger hashing algorithms and additional security measures like message sequencing to enhance protection against replay attacks.
	- Limitation of CHAP and CHAPv2
		- Used in PPP connection
		- Not very common today like EAP (Extensible Authentication Protocol)
- EAP (Extensible Authentication Protocol)
	- How it works
		- **Initiation:** The client attempting access sends an EAP request to the authentication server.
		- **Method Selection:** The server proposes a list of supported EAP methods to the client.
			- **EAP-TLS (Transport Layer Security):** Uses digital certificates for secure authentication, often used for secure connections like VPNs.
			- **PEAP (Protected EAP):** Encapsulates another authentication method (often MS-CHAPv2) within a TLS tunnel for added security.
			- **EAP-TTLS (Tunneled TLS):** Similar to PEAP, but offers more flexibility in choosing the inner authentication method.
			- **EAP-SIM (Subscriber Identity Module):** Utilizes SIM cards commonly found in mobile devices for authentication.
			- **EAP-OTP (One-Time Password):** Employs one-time passwords generated by software tokens or hardware tokens for enhanced security.
		- **Method Negotiation:** The client chooses a mutually supported EAP method from the list and sends a selection back to the server.
		- **Method-Specific Exchange:** Based on the chosen method, a series of challenges and responses are exchanged between the client and server for authentication.
		- **Access Granted/Denied:** After successful authentication via the chosen EAP method, the server grants access to the requested resource.
	- EAP is used nowadays in Wi-fi, VPNs, network access control
	- EAP-TLS
		- **Initiation:** The client sends an EAP request to the server, indicating its desire to use EAP-TLS for authentication.
		- The server sends its digital certificate to the client. This certificate verifies the server's identity and is issued by a trusted Certificate Authority (CA).
		- The client verifies the server's certificate and sends its own digital certificate to the server. This certificate verifies the client's identity (user or device).
		- Both the client and server establish a secure TLS session using encryption keys derived from their respective certificates.
- PAKE (Password-Authenticated Key Exchange)
	- PAKE (Password-Authenticated Key Exchange) is a cryptographic protocol designed to establish a secure communication channel between two parties based solely on their knowledge of a shared password. This eliminates the need for pre-distributed keys or certificates, making it a convenient and efficient solution for certain scenarios.
	- Advantages: Traditional methods transmit passwords during authentication, but i can be vulnerable to breaches. So this method overcomes by using DH Key Exchange
	- Principles
		- **Diffie-Hellman Key Exchange (Foundation):** PAKE leverages the Diffie-Hellman key exchange concept, where two parties publicly exchange random values to derive a shared secret key without needing a pre-shared secret.
		- **Challenge-Response Mechanism:** Each party generates a random challenge and sends it to the other party. These challenges are used in conjunction with the password to compute responses.
		- **Verification of Password Knowledge:** The responses exchanged during the challenge-response mechanism implicitly verify that both parties know the correct password.
		    - Even though the actual password is not transmitted, the responses mathematically depend on the password, ensuring only parties with the correct password can compute valid responses.
	- JPAKE (Password Authenticated Key Exchange by Juggling)
		- **Password Authenticated Key Exchange by Juggling(J-PAKE)** is a _password-authenticated key agreement(PAKE)_ protocol without requiring **Public Key Infrastructure(PKI)** for authentication. _J-PAKE_ is able to establish a private and authenticated channel on top of an insecure network solely based on a shared password.
		- _J-PAKE_ use [_Zero-Knowledge Proof_](https://chunminchang.gitbooks.io/j-pake-over-tls/content/appendix/zkp/zkp.html "Zero-Knowledge Proof") to produce valid knowledge proof of a discrete logarithm without revealing it. One example is to use [Schnorr digital signature](https://chunminchang.gitbooks.io/j-pake-over-tls/content/appendix/zkp/schnorr_signature.html "Schnorr signature"), which is a non-interactive protocol.
		![[Pasted image 20240424211124.png]]
		![[Pasted image 20240424211731.png]]
		![[Pasted image 20240424211918.png]]
		![[Pasted image 20240424220802.png]]
		![[Pasted image 20240424221857.png]]
	- Augmented PAKE (klient/server komunikace, kdy server nezná hesla, ale např. jen hash z hesla
		![[Pasted image 20240424222135.png]]
		![[Pasted image 20240424222209.png]]
- Autentizační protokoly a mechanismy pro čipové karty a moduly SAM
	- Autentizační protokoly využívají většinou standardních kryptografických schémat (TDES, AES, RSA, atd.).
	- U levných čip. karet je snahou sestavovat aut. protokoly založené na symetrické kryptografii a jednoduchých operací – omezený klíčový management
	- Mezi základní bezpečnostní požadavky patří
		- Jednostranná autentizace.
		- Odolnost proti padělání.
		- Odolnost proti útoku paralelní relace. SCHÉMAT 
		- Odolnost proti útoku zopakování zprávy (v a.j. Replay attack). 
		- Odolnost proti kompromitaci ověřovatele. 
		- Odolnost proti kompromitaci serveru. 
		- Odolnost proti útokům odepření služeb. 
		- Odolnost proti offline hádání hesla/tajemství
	- Nadstandardní bezpečnostní požadavky: 
		- Vzájemná autentizace. 
		- Odolnost proti útoku při ztrátě karty. 
		- Zpětné zabezpečení (v a.j. Perfect forward secrecy). 
		- Ustanovení klíče. 
		- Zajištění uživatelské anonymity. 
		- Odolnost proti útoku zevnitř.
	- Útoky
		- MIFARE CRYPTO 1: Malá velikost klíče - 48 bitů útok hrubou silou, cca 4 roky na PC,  minuty na FPGA.
	- Protokol PACE (Password Authenticated Connection Establishment)
		- Protokol pro bezpečné ustanovení šifrovacích klíčů při znalosti správného hesla pro následnou zabezpečenou komunikaci.
		- PACE protokol využívá hash funkce, symetrickou kryptografii, eliptické křivky v kombinaci s Diffie-Hellman algoritmem a autentizační kódy MAC. 
		- Heslo zadává uživatel pak na čtečce.
	- Protokol EAC (Extended Access Control)
		![[Pasted image 20240424223905.png]]
		![[Pasted image 20240424223919.png]]
5. Autentizační předměty a zabezpečené hardwarové moduly
- Autentizační předměty
	- Definice
		- předměty používané uživateli v rámci autentizace při žádosti o přístup do systému.
		- Karta, klíčenka
		- Autentizace předmětem je často kombinováno s autentizací znalostí (PIN, heslo) nebo autentizací biometrikou (otisk prstu) za účelem zvýšení bezpečnosti přístupového systému.
	- Předměty musí být chráněny proti falzifikaci a klonování.
	- Používáme RFID Tagy (čip): Radio Frequency Identification, identifikace na rádiové frekvenci (RFID) – slouží k identifikaci zboží, předmětů, strojů, zvířat, lidí
		- Pasivní Tag
			- RFID tag přijímá energii od vysílače (nabíjí se napájecí kondenzátor) a odesílá odpověď (číslo EPC + další data) – systémy Active Reader Passive Tag (ARPT)– nízké náklady (desítky korun)
		- Aktivní Tag
			- RFID tagmá vlastní zdroj (baterie) a může sám aktivně vysílat, často větší paměť a kryptoprocesor (AES, TDES, RSA, SHA), použito v aktivní lokalizaci - Active Reader Active Tag (ARAT)– (cena: sto a více korun).
		- RFID nesou 96-bitové unikátní číslo EPC (Electronic Product Code)
		- Výrobní třídy tagů– zápis dat
			- Class0 –read-only, data jsou zapsána při výrobě.
			- Class1 -One-Time Programmable(OTP), data lze jednorázově zapsat na TAG. 
			- Class1 GEN2 –data lze zapsat, TAG lze uzamknout proti dalšímu zápisu, obsahuje i CRC kontrolu.
		- Útoky
			![[Pasted image 20240425093934.png]]
		- Tyhle útoky řešil EPC Gen 2
			- Skrytí tagu – pouze oprávněné čtečky mohou načíst data a detekovat tag
			- Šifrování dat – od gen 2 verze 2, AES-128 a Grain-128A (staticky zašifrovaný obsah).
	- Čipové karty
		- Integrated Circuit Card (ICC) - slouží jako autentizační předměty uživatele nebo jako nosiče aplikací
		- Použití
			- Přístup do chráněných prostor. 
			- Platby, EMV (Europay, MasterCard,Visa) karty. 
			- E-ticketing. 
			- Debitní karty.
		- Typy
			- Paměťové–integrovaný obvod (ukládání dat a volitelné zabezpečující mechanismy), 
			- procesorové–paměťové +procesor (Smart karty), 
			- kryptografické– procesorové + kryptografický koprocesor (RSA, AES, SHA,…), 
			- programovatelné– (JAVA Smart Cards, .NET Smart Cards, MultOS,…) – více viz další přednáška.
		- Komunikační rozhraní
			- Kontaktní
			- Bezkontaktní
			- Hybridní
		- Útoky
			- Odposlech dat u bezkontaktního rozhraní – šifrování komunikace mezi čtečkou a kartou. 
			- Falešná čtečka/ověřovatel – nutnost vzájemné autentizace. 
			- Falešná karta/uživatel – karta nesmí být snadno klonovatelná či snadno padělatelná – bezpečná autentizace, dobrá HW ochrana. 
			- Útoky zneužívající slabé klíče a špatně vygenerované náhodné čísla zvýšení kvality generování klíčů či hodnot – externí generování klíčů. 
			- Invazivní útoky a útoky postranními kanály – SW a HW ochranné metody jako např. přidání tzv. dummy funkcí, počítaní v konstantním čase atp.
	- USB tokeny
		- USB kontakt, někdy i LCD displej. 
		- Parametry = flash disk / smart card 
		- Úložiště (chráněné): ‐ soukromé klíče,‐ certifikátů,‐ jednorázové hesla OTP (data+čas), ‐ licenčního kódu,‐ tajných dat pro výzva/odpověď.
	- Mobilní telefony
		- Výpočetní výkonost je mnohem vyšší než smart karty. 
		- Problém s chráněným uložištěm (tzv. secure element). 
		- Vývoj e-payment, autentizačních aplikací.
		- Pomocí telefonu s NFC lze číst bezkontaktní čipové karty -> telefon jako čtečka 
		- Anténa na zadním krytu či na baterce.
	- Mobilní telefony s NFC – větší riziko výskytu malware a dalších bezpečnostních problémů než u omezených čipových karet.
- Zabezpečené hardwarové moduly
	- Subscriber Identity Module SIM
		- integrovaný obvod s OS, pamětí a čipem pro bezpečné uložení čísla IMSI (International Mobile Subscriber Identity), 128-bitového klíče uživatele Authentication Key (Ki) a dalších parametrů.
		- Hlavní účel je autentizace uživatele s mobilním telefonem v 3 – 5G sítích
		- Složení IMSI: 
			- První 3 digity tvoří Mobile Country Code (MCC), 
			- Další 2 až 3 digity tvoří  Mobile Network Code (MNC), 
			- Zbývají tvoří Mobile Subscriber Identification Number (MSIN)
		- Útoky
			- Naivní – změna PINu u nezamčených telefonech.
			- Klonování SIM – útočník, pokud se zmocní SIM a podaří se mu ji naklonovat, pak může přijímat SMS a hovory oběti (ta zůstane mimo dokud nenabootuje znovu), nyní existuje i služba MultiSIM format, kdy je možné využívat stejnou SIM ve více zařízeních.
			- Extrahování Ki (výpočet z dostatečného počtu SRES odpovědí z A3  COMP128v1 algoritmu při autentizaci), COMP128v3 algoritmus se zdá odolnější.
	- Secure Access Module SAM
		- bezpečný přístupový (aplikační) modul.
		- Rozšiřuje kryptografické funkce (generování klíčů, podpis, šifrování, ověřování) a jejich výkonost v jednodušších zařízení jako jsou komunikační brány, ověřovací terminály, smart metery atp. 
		- Nabízí bezpečné úložiště pro hlavní a soukromé klíče. 
		- Založen většinou na smart kartách (podobné HW a SW parametry).
	- Secure Element SE
		- zabezpečené úložiště dat v mobilních zařízeních, které by pomocí NFC mohli poskytovat stejné funkce jako bezkontaktní čip. karty.
	- Trusted Platform Module (TPM)
		- zabezpečený kryptoprocesor– čip, který je montován k základní desce u téměř většině počítačů, notebooků a i mnoha mobilů, set top boxů, konzolí atd
		- Účel
			- zajistit integritu platformy (OS), společně s BIOSem (režim UEFI) tvoří tzv. Root of trust – kořen důvěry – bezpečný start OS, 
			- generování šifrovacích klíčů a jejich uložiště, 
			- uložení jedinečného soukromého klíče RSA a dalších klíčů a certifikátů, o provádění kryptografických funkcí, 
			- vzdálené ověření (Remote attestation) HW a SW konfigurace a jejich změn u autorizovaných partnerů (třetích stran), 
			- pomáhá ukládat klíče pro šifrování data na disku (Bitlocker), 
			- pomáhá při autentizaci v kombinaci s technologií VSC (Virtual Smart Card)
			- pomáhá chránit hesla a proti malware,
			![[Pasted image 20240425102035.png]]
		- Implementace TPM 2.0
			![[Pasted image 20240425102229.png]]
			- DiskrétníTPM - dedikované tamper-resistant čipy. Nejvíce bezpečné.
			- IntegrovanýTPM- součást jiného čipu. HW odolný SW zranitelnostem. Např.. Intel chipset s TPM. 
			- Firmware TPM-software-only řešenípro běh CPU's v důvěrném prostředí. Mohou být vystaveny SW zranitelnostem. Např. AMD, Intel Platform Trust (PTT), Qualcomm TPMs. 
			- Software TPM-software emulator TPM, který běží ve více chraněném režimu než běžné programy na OS.  Nejsou příliš bezpečné, náchylné na útoky a SW zranitelnosti. 
			- Virtualní TPM –běžící v hypervisoru. Podobné jako Firmware TPM.
		- Útoky
			- TPM-v 2015 Snowden odhalil, že tajné klíče na TPM bylo možné získat pomocí diferenční proudovou analýzou postranním kanálem.
	- Hardware Security Module (HSM) - hardwarový bezpečnostní modul
		- Jedná se fyzickou výpočetní jednotku určenou pro management klíčů, silnou autentizaci, PKCS#11 a provádění kryptografických operací (RSA, ECIES, ECDSA, AES,…). o Plug-in karty nebo externí zařízení připojené k PC či serveru (nejedná se tedy o chip jako TPM).
		- Obsahuje vlastní paměťové moduly a bezpečný kryptoprocesor, který je tamper-resistant, senzory detekce průniku.
		![[Pasted image 20240425102520.png]]
	- Útoky
		- Meet in the Middle: 
		![[Pasted image 20240425102625.png]]
6. Programovatelné čipové karty
- Popis
	- Chytré čipové karty (CPU+paměť + KARTY bezpečnostní funkce) – smartkarty– hostí aplikaci/e
	- Programovatelné čip. karty umožňují tvorbu vlastních aplikací a liší se podle OS/platformy, např.: 
		- JAVA Smart Cards, .NET Smart Cards (C#), MultOS (jazyk C), BASIC…
	- Rozsáhlé data se ukládají spíše na server – karta nese jen základní aplikační logiku a autentizační informace k účtu (tajné a privátní klíče) – útočník musí pak útočit přímo na kartu.
- Protokol přenosu dat mezi čtečkou a čip. kartou
	- APDU (Application Protocol Data Unit)
	- The ISO/IEC 7816 standard defines a set of commands and instructions that can be used to interact with smart cards. These commands cover a wide range of operations such as reading data from the card, writing data to the card, verifying PIN codes, and executing cryptographic algorithms.
	- The APDU protocol includes mechanisms for ensuring the security of communication between the card reader and the smart card. This includes features such as authentication, encryption, and integrity checks to prevent unauthorized access and tampering of data.
- Platforma JAVA Card
	- nejrozšířenější platforma programovatelných karet, např. ATM karty, SIM karty
	- JAVA applety mohou běžet na různých smart kartách, které poskytují JAVA Card OS přenositelnost.
- Platforma MultOS Card
	- Programovatelné čipové karty MultOS- multi-application smart card operating system. •
	- Podpora více aplikací na kartě. Podpora standardů ISO 7816, EMV. 
	- Bezpečný ekosystém pro vydávání aplikací a karet. 
	- Vývoj v C, JAVA, asembleru, kompilace do MULTOS Executable Language (MEL)  - Reduced Instruction Set Computer (RISC)
- Platforma BASIC Card a .NET Card
7. Reverzní inženýrství a softwarová bezpečnost 
- Softwarová bezpečnost
	- Padá do oblasti Computer Security: se zabývá jak zajistit a udržovat požadované vlastnosti počítačových systémů v přítomnosti inteligentního útočníka snažící se ho o narušení vlastností.
	- Softwarová bezpečnost patří do oboru počítačové bezpečnosti a zabývá se jak útočník může zneužít (exploitovat) program/SW systému a jak vývojář může zabránit zneužití (exploitů).
	- Softwarové hrozby
		- Malware– škodlivý SW který se snaží využít chyb jiného SW či OS a škodit v SW prostředí. Typicky se jedná o: 
			- Počítačový červ – šíří se bez interakce uživatele. 
			- Počítačový vir – škodí v OS, většinou je spuštěn uživatelem. 
			- Ransomware–program snažící se vydírat uživatele s hrozbou smazání dat či jejich zašifrování. 
			- Rootkit–sada programů které se snaží maskovat přítomnost zákeřného softwaru v počítači, skrývat procesy, soubory atd. 
			- Backdoor–program/metoda umožňuje obejít běžnou autentizaci, která za běžných okolností brání uživateli v neoprávněném využívání počítačového systému. 
			- Spyware–program detekující a přeposílající uživatelské data bez jeho vědomí, např. keylogger, adware, hijacker,dialers… 
			- Trojský kůň – program/SW/soubor, který se jeví jako neškodný pro uživatele, ale ukrývá různé kombinace škodlivého malware jako je key logger, vir, červ, backdoor, ransomware, rootkit. 
			- Logická bomba –kód, který je vložen do programu, který se spustí po splnění podmínek a má za cíl škodit (provést payload, např. smazat soubory).
		- DoS
		- DDoS
		- Změna webového GUI na web grafiti
	- Zranitelnosti a SW chyby pro zneužití
		- Zranitelnosti (vulnerability) jsou v SW bezpečnosti vnímány jako slabiny v OS či konkrétním SW (desktopové aplikace, webové aplikace, systémové aplikace, aplikace na různých platformách), které může útočník zneužít pro napáchání škod
		- Obecné typy zranitelností: 
			- Bezpečnostní chyba v programu (bug) – dílčí programátorská chyba, která dále může zapříčinit zranitelnost a následně být zneužitelná útokem. 
			- Kromě chyb se může jednat i o systémové chyby vycházející ze špatného návrhu, konfigurace atp. 
			- Zranitelnost typu Zero-day (0-day) je označována jakákoliv doposud neznámá zranitelnost. Dokud není odstraněna (patch, update), tak útočník může tuto zranitelnost zneužívat.
		- Klasifikace podle Red Hat a MS Windows: Vyhodnocení podle CVSS (verze 3)
			- Minimální dopad (low) 
				- zneužití je obtížné, nebo se jedná pouze o minimální dopad. 
			- Průměrné (moderate)
				- zneužití se zmírněno implicitním nastavením, obtížností, auditováním (záznamem operací), 
				- k problému může dojít, ale jsme schopni ho včas detekovat a postarat se o včasný zásah. 
			- Důležité (important) 
				- ohrožení uživatelských dat nebo systémových prostředků, 
				- například nám někdo nainstaluje do počítače malware, který začne rozesílat spam. 
			- Kritické (critical)
				- vzdálený útok, kdy se do systému dostane útočník zvenku,
				- např. ohrožení síťovým červem bez účasti uživatele, umožnění backdoor,…
		- Jsou databáze a seznamy zranitelností pro nás
			- CVE (CommonVulnerabilities and Exposures)
			- CWE (Common Weaknesses Enumeration)
			- NIST NVD (NATIONAL VULNERABILITY DATABASE)
			- OSVDS (Open Source Vulnerability Database)
	- Skupiny SW zranizelností
		![[Pasted image 20240426090521.png]]
		![[Pasted image 20240426091331.png]]
	- Realizace softwarové bezpečnosti
		![[Pasted image 20240426105912.png]]
	- Životní cyklus bezpečnosti SW (SDLC)
		![[Pasted image 20240426110459.png]]
		![[Pasted image 20240426110519.png]]
- Reverzní inženýrství a invazivní a neinvazivní útoky
	- Jedná se o proces, jehož cílem je odkrýt princip fungování zkoumaného předmětu (softwaru). 
	- Rozšířená definice: Proces analýzy předmětného systému s cílem identifikovat komponenty systému a jejich vzájemné vazby a/nebo vytvořit reprezentaci systému v jiné formě nebo na vyšší úrovni abstrakce.
		![[Pasted image 20240426110843.png]]
	- Kompilace a dekompilace kódu
		- Kompilátory: překlad kódu programu (vyššího jazyka) do strojového kódu (např. do binárního souboru). 
		- Dekompilace je zpětné přeložení binárního kódu na výstup původního jazyka.
		- Dissasembler překládá strojový kód do symbolického zápisu v assembleru. 
		![[Pasted image 20240426111046.png]]
		- Dekompilace
			- Cílem je dekompilovat binární program na vyšší původní programovací jazyk za účelem jeho porozumění.
			- Vstup: 
				- Platformě závislý binární program. 
				- Popis platformy. 
			- Výstup: 
				- Uniformní výstup v jazyku vyšší úrovně (např. C, JAVA). 
				- Dissemblovanýkód. 
				- Grafická prezentace (graf toku řízení a volání). 
				- Statistiky. 
			- Náročnost dekompilace je závislá nad použitou obfuskací a dodatečnou ochranou. 
				- Jednoduší dekompilace se považuje u JAVA a #C, oproti C.
			- Problém dekompilace
				- Ztráta informací a metadat vlivem optimalizace (komentáře, makra, direktivy, typy, znaménkovost, vysokoúrovňové konstrukce, jména proměnných, jména funkcí atd.). 
				- Přídavné ochrany: obfuskace kódu a binárky, anti-debugging ochrany.
				- Mnoho programovacích jazyků a překladačů 
					- Např. pro C: GCC, Clang, MSVC, ICC, … 
				- Různá binární rozhraní (zarovnání datových typů, mnoho způsobů v asembleru jak udělat stejnou funkci).
				- Různé souborové formáty
			- Nástroje
				![[Pasted image 20240426111709.png]]
	- Ochrana proti zpětnému inženýrství
		- Mezi obecné ochrany patří: 
			- obfuskacekódu, 
			- anti-debugging ochrany, 
			- šifrování, 
			- hardwarové klíče, 
			- další kryptografické prostředky. 
		- Typické vývojářské ochrany: 
			- Obfuskacekódu: 
				- změna jmen funkcí,  
				- změna sekvencí kódu, extra skoky, 
				- pseudopodmínky. 
			- Injektacekódu. 
				- přidání šumu – funkcí které nemají vliv (tzv. dummy). 
			- Polymorfismy, sebe-modifikace, code morphing
	- Invazní a neinvazní útoky
		![[Pasted image 20240426112024.png]]
		![[Pasted image 20240426112047.png]]
		![[Pasted image 20240426112123.png]]
8. Postranní kanály - úvod do problematiky
- Definice
	- A side-channel attack is a security exploit that targets information leakage from a system, rather than exploiting weaknesses in the cryptographic algorithm itself.
	- Instead of focusing on breaking the encryption itself, side-channel attacks attempt to extract secret information (like encryption keys) by analyzing indirect emissions or behaviors of the system performing the encryption or decryption.
- How the information leaks:
	- The attacker studies the system's behavior to understand how it leaks information through side channels. This might involve setting up special equipment to monitor power consumption, electromagnetic emissions, or timing the execution of cryptographic operations.
		- After measuring, they perform statistical analysis, and then extracting secrets (reconstructing the secret information)
	- **Timing:** How long a cryptographic operation takes (e.g., encryption/decryption time might vary depending on the data being processed).
	- **Power Consumption:** The amount of power a device consumes during cryptographic operations (fluctuations in power usage might reveal information).
	- **Electromagnetic Emissions:** Electromagnetic waves emitted by the device during processing (can be picked up by specialized equipment).
	- **Acoustic Emissions:** Sounds produced by the device during cryptographic operations (extremely rare, but possible).
- Časová analýza (TA)
	- Měření a analýza doby, která je potřebná k vykonání určitých operací v kryptografickém modulu
	- Ten útok je realizovatelný když existuje souvislost mezi senzitivní informací (klíč) a dobou výpočtu
	- Příklad:
		- Algoritmu verifikaci hesla
			![[Pasted image 20240428100126.png]]
			![[Pasted image 20240428100748.png]]
		- Implementace algoritmu RSA (modulární násobení)
- Proudová analýza (PA) - základní princip
	- Studuje proudovou spotřebu kryptogradického modulu v závislosti na jeho činnosti
	- V dneční době představuje efektivní a úspěšný způsob útoku cílený na algoritmy AES nebo RSA
	- Komplexní problematika obsahující měření proudové spotřeby, znalost kryptografických algoritmů, zpracování signálu, statistiku
		![[Pasted image 20240428101826.png]]
- Elektromagnetická analýza (EMA)
	- Následkem nabíjení a vybíjení parazitní kapacity (invertor) vzniká v obvodu skoková změna proudu
	- Projevující se emitací elektromagnetického pole
- Akustická analýza
	- Útoky na klávesy psacího stroje, tiskárna
- Optická analýza
	- Při změně stavu doje k vyzáří několik fotonů
9. Bezpečnost na chytrých zařízeních
- Bezpečnost chytrých zařízení (smartphone, smartwatch, smartglasses, platforma Android).
	- Android:
		- Android je mobilní operační systém (OS) založený na Linuxovém jádře
		- Vývoj v jazyce JAVA (Kotlin nebo C/C++ v NDK)
	- Útoky
		- Software
			- Malicious applications with too much permissions
			- Application elevating privileges
			- Exploited vulnerable application or browser
		- Physical attacks
			- ADB enabled, can allow app with all permissions and extract data
			- Dump with hardware technique
	- Ochrana zařízení
		- Autentizace
			- Záměk obrazovky
				- PIN
				- heslo
				- Otisk prstu
				- Vzor
			- SmartLock
		- Šifrování souboru, disku
		- Omezení přístupu uživatelům
- Bezpečnost komunikačnách protokolů (WiFi, BLE - Bluetooth Low Energy, NFC - Near Field Contact)
		![[Pasted image 20240429160631.png]]
		![[Pasted image 20240429160648.png]]
		![[Pasted image 20240429160721.png]]
10. Metodiky hodnocení bezpečnosti zařízení a systémů
- Úvod do hodnocení bezpečnosti, normy
	- Kybernetická bezpečnost: 
		- Softwarová bezpečnost. 
		- Počítačová bezpečnost - bezpečnost OS a dat. 
		- Sítová bezpečnost - bezpečnost komunikačních protokolů a rozhraní. 
		- Fyzická bezpečnost, přístupové a dohledové systémy. 
		- Bezpečnost procesů a řízení bezpečnosti informací. 
	- Hodnocení bezpečnosti by mělo korespondovat s předpisy a normami.
- Procesní řízení bezpečnosti
	![[Pasted image 20240429162622.png]]
- Normy rodiny ISO/IEC 27K
	![[Pasted image 20240429163105.png]]
- Metodiky hodnocení bezpečnosti zařízení a systémů
	- Common Criteria
		![[Pasted image 20240429163312.png]]
		![[Pasted image 20240429163359.png]]











