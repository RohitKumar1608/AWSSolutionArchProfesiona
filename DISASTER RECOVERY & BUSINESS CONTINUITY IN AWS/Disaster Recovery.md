****DR/BC Architecture****

  -  Effective DR/BC costs money all of the time
  -  We need some type of extra resources which will increase costs
  -  Executing disaster recover/business continuity process takes time. How long it takes depends on the type of DR/BC in usage
  -  DR/BC is trade-off between the time and costs

<img width="1440" alt="Screenshot 2024-05-20 at 7 32 17 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/676eba7f-081c-4cac-8fe1-d31c8ff1c1eb">

******Types of Disaster Recovery******

****Backup and Restore:****
  - Data is constantly backup up at the primary site
  - The only costs are backup media and management, no ongoing space infrastructure costs
  - Has little or no upfront costs, but implies a significant time for recovery

<img width="1440" alt="Screenshot 2024-05-20 at 7 37 45 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/df1cc54f-a799-4a6f-bf6c-883cb545a3a1">

****Pilot Light::****
  - Primary site is running at full
  - Pilot Light implies running a secondary environment only having the absolute minimum services running
  - In the event of a disaster the shutdown services can be spined up, no costs are expected to be inquired if there is no need for DR

<img width="1440" alt="Screenshot 2024-05-20 at 7 41 35 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/549e7d13-fa0c-4961-b121-fb9790b0df7d">

****Warm Standby:****
  - Primary site is running at full, everything is replicated on the backup site at a smaller scale
  - Ready to be increased in size when failover is required
  - It is faster than pilot light approach and cheaper than active/active approach

<img width="1440" alt="Screenshot 2024-05-20 at 7 48 55 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/19079e39-a907-4353-a9fe-5fedfbc20979">


****Active/Active (Multi-site):****
  - Primary site is entirely replicated on a secondary site
  - Data is constantly replicated from the primary site to the backup
  - Costs are generally 200%
  - There is no concept of recovery time

 **Additional benefits:**
    - Load balancing across environments
    - Improved HA and performance

<img width="1440" alt="Screenshot 2024-05-20 at 7 51 41 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/7c6d5970-8c8c-41f1-bd63-3965ea85d9d1">

****Summary:****
  - Backups: cheap and slow
  - Pilot Light: fairly cheap but faster
  - Warm Standby: costly, but quick to recover
  - Active/Active: expensive, 0 recovery time

<img width="1440" alt="Screenshot 2024-05-20 at 7 54 26 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/c89d4971-976a-4c77-834c-b0fbd538e22d">
