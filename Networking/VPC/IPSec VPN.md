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
        - Agree encryption method, and keys used for bul transfer
        - Create IPSec SA(Security Association) -- phase 2 tunnel(architecturally rnning over phase 1)
