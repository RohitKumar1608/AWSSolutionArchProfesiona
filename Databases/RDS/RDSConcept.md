### RDS Architecture
<img width="1440" alt="Screenshot 2024-05-04 at 7 11 55 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/262ef3d6-d1e2-4a47-bb73-97d18ab5e441">
<img width="1440" alt="Screenshot 2024-05-04 at 8 53 32 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/cc4cb2f5-e7ea-4265-8c0c-9f1f8f56b3e8">
****Notes :- ****

      - Each DB instance Can have 1 or More DB
      - Primary and Stand will be placed in different AZ 
      - Each DB have their EBS Storage.
      - Synchronous Replication between Primary and Standby
      - Asynchronous Replication between Standby and Read Replica.
      - Read Replica can be in same region or different regions.

<img width="1440" alt="Screenshot 2024-05-04 at 8 57 23 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/6196174c-5da8-4083-b5c1-f35f508a2022">
<img width="1440" alt="Screenshot 2024-05-04 at 10 05 33 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/7f75a961-9018-4ce0-add4-327afca3138f">****RDS Multi-AZ******
<img width="1440" alt="Screenshot 2024-05-04 at 10 07 22 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/1df9bafe-346a-4a76-b5b4-67aeecada7b0">
### RDS - Multi-AZ Cluster
****Notes******

      - 2 Readers only in different AZ
      - Writer -> Synchronously writes to the 2 Readers
      - From Instance Mode , in Multi AZ Cluster mode Readers are usable.
      - Writer Can be used for Read and Write . Reader can be used only for the Read operations.
      - Data is committed when at least one of the reader confirms writing is finished.
      - Different that Aurora Cluster :- In RDS Multi AZ Cluster mode , Each instance has its own storage.
      - Like Aurora , Access of the Cluster through the endpoints
                - Cluster endpoint :- Database CNAME Points at the Writer and can be used for the read and Write
                - Reader endpoint :- Directs any reads at an available reader instance
                - Instance endpoint :- Points to specific instance . Used for testing and Fault finding.


<img width="1440" alt="Screenshot 2024-05-04 at 10 36 40 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/d2e8e7d6-e369-413c-bf6a-bc1740152462">
<img width="1440" alt="Screenshot 2024-05-04 at 10 39 27 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/e4521e7a-7f5b-468f-80d6-36a37def5315">
