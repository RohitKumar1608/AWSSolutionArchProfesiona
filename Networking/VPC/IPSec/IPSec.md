1. IPSec is a group of Protocols. It sets up secure tunnel over insecure networks.
2. IPSec provides Athentication.
3. Traffic using IPSec are encrypted.
4. Interesting traffic - Traffic matching specific rules then the tunnel is created else it is torn down.

IPSec understanding -------------------------------------------------------------------------------------------
IPSec has two main phases 
   1. IKE Phase1 (Slow and Heavy)
        - Athenticate - Pre-shared key password/Certificate
        - Using Asymmetric encryption to agree on, and create a shared symmetric key
        - IKE Security Association created(phase 1 tunnel)
   2. IKE Phase 2(Fast & Agile)
        - Uses the keys agreed in phase1
        - Agree encryption method, and keys used for bulk transfer
        - Create IPSec SA(Security Association) -- phase 2 tunnel(architecturally rnning over phase 1)

IKE Phase 1 Steps --------------------

1. Proof the identity on either side of Site with certificate and Pre-shared Key authentication.
2. Diffie Hellman key exchange is the next step - Each side create a DH private key. This key is used tp decrypt data and sign things.
3. In addition , each side uses the private key and derive the corresponding public key.Public key can be used to encrpt data but only the private key can decrypt.
4.  public keys are exchanged over internet.
5.  Each side take their private key and the remote shared public key to  independently    derive the same share DH key.
6.  using DH key- other key material and aggrements are exchanged.
7.  Each side independently use the DH key and the key material to generate a symmetrical key.This key is used to encrypt phase 1 tunnel.

   The process seems slow and heavy.

IKE Phase 2 Steps - gettting the VPN up and running ------------------------
DH key, Symmetric Keys and IPSec SA tunnel 1

1. Symmetric key is used to encrypt and decrypt aggrements and pass more key material by peer1
2. Other Peer will pick the best shared encryption and integrity methods communicated and agreed.
3. DH key + Exchange key material is used to generate the symmetrical IPSec key. Designed for large scale data transfer.
4. IPSec key is used for bulk encryption and decryption of the interesting traffic.Provide less functionality but simple to setup.

Types of VPN -------------------------------------------
1. Policy Based :- Rule sets match traffic.Based on the rule traffic is sent over the pair of SAs. Different rules for different type of traffic
2. Route Based :- Target matching based on prefix. Single pair of SAs for each network prefix.
