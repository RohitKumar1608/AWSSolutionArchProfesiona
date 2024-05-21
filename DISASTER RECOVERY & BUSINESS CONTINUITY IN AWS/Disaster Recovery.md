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


****DR Architecture - Storage****

 ****Instance Store volumes:****
 
    - Most high risk form of storage available
    - If the host fails, the instance store volumes will also fail
    - Should be viewed as temporary and unreliable storage

 ****EBS:****
 
    - Volumes are created an run in a single AZ (failure of AZ means failure of EBS volumes)
    - Snapshots of EBS are stored in S3, will increase reliability

 ****S3:****
 
    - Data is replicated across multiple AZs
    - One-Zone: not regionally resilient

 ****EFS:****
 
   - EFS file systems are replicated across multiple AZs
   - They are by default regionally resilient - failure of a region means failure of EFS volumes


<img width="1440" alt="Screenshot 2024-05-20 at 10 03 12 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/e3b9bba2-6814-4e4c-88a4-2d238cae3c29">

****DR Architecture - Compute****

 **EC2:**
 
    - If the host fails, EC2 instances fails as well
    - An EC2 instance by itself is not resilient in any way
    - If the failure is limited to one host, the instance can move to another host in the AZ. The EBS volume can be presented to the          new instance
    - Auto Scaling Group: can be placed in multiple AZs, if the instance fails in one AZ, the ASG's role is to recreate them in another

****ECS:****

   - Can run it 2 modes: EC2 and Fargate
   - EC2 mode: DR architecture is similar as above
   - Fargate mode: containers are running on a cluster host managed by AWS being injected in VPCs
   - Fargate can provide automatic HA by running things in different AZs

****Lambda:****

  - By default runs in public mode
  - In VPC mode (private) Lambdas are injected in VPCs. If an AZ fails, Lambda can be automatically injected in another subnet in a         different AZ
  - It will take the failure if a region in order for Lambda to be impacted

<img width="1440" alt="Screenshot 2024-05-20 at 10 16 31 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/abc03df3-08cf-49eb-8136-db05d393c627">
