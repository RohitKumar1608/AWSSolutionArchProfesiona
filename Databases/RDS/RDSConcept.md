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

****RDS - Backup and Restore****

****Notes******

      Two Types Backup type functionality
  	      - Automated Backup
  	      - Manual Snapshots

          - Both these are stored in S3. These buckets are managed by AWS.Won’t be visible in the AWS Console.Backup can be seen in RDS but              not in S3.
          - Snapshot don’t expire that means you have to clean it once the RDS instance is deleted.
          - Automated Backup once per day. Architecture is same :- First one is full ,subsequent is incremental.
          - Every 5 min database transaction logs is also written to S3. Transaction logs has the details of the Operation performed on the              DB
          - Recovery Point objective - 5min
          - Retention Period is from 0 t0 35 days. 0 means Automated backup disabled. 

<img width="1440" alt="Screenshot 2024-05-04 at 3 50 06 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/128925c8-c0bd-44a2-a4c6-cb45fcd857d7">
<img width="1440" alt="Screenshot 2024-05-04 at 3 55 23 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/fdea8014-98a0-40ad-a56c-a89afe34190b">
<img width="1440" alt="Screenshot 2024-05-04 at 3 57 03 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/9f2110e2-8778-419f-bae8-f6935fbe2f17">

****RDS - Read Replicas****
<img width="1440" alt="Screenshot 2024-05-04 at 4 26 40 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/5a445b41-a710-4ec0-8097-4813a4351922">
****Why Read Replicas????****
<img width="1440" alt="Screenshot 2024-05-04 at 4 27 47 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/a4ad9f44-0776-40db-b93e-227e1541586b">
<img width="1440" alt="Screenshot 2024-05-04 at 4 29 13 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/1c5a4765-5573-47d9-8dd7-47a3921c3696">

****RDS - Security****
       - Authentication
       - Authorization
       - Encryption in Transit
       - Encryption t Rest
Encryption at Rest :-  depends on the database instance. 
RDS supports EBS volume encryption - KMS

<img width="1440" alt="Screenshot 2024-05-08 at 10 53 33 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/8a9e42f2-ab33-4ef3-bf27-12605752a7df">
<img width="1440" alt="Screenshot 2024-05-08 at 10 55 06 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/6964bd16-5c96-41e2-b9ef-853c79fad8a2">
<img width="1440" alt="Screenshot 2024-05-08 at 11 02 54 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/b5bf5c2c-1ea2-4fa8-9c35-aa1d801a37b9">

