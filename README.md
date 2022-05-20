# Build-and-Secure-Networks-in-Google-Cloud-Challenge-Lab


# TASK 1: Remove the overly permissive rules
    gcloud compute firewall-rules delete open-access
    
# TASK 2: Start the bastion host instance
**Go to VM instances and start the Bastion instnce**


# TASK 3: Create a firewall rule that allows SSH (tcp/22) from the IAP service and add network tag on bastion
    gcloud compute firewall-rules create ssh-ingress --allow=tcp:22 --source-ranges 35.235.240.0/20 --target-tags [NETWORK TAG-1] --network acme-vpc

    gcloud compute instances add-tags bastion --tags=[NETWORK TAG-1] --zone=us-central1-b
 <Replace network tag 1 with SSH IAP network tag >
 
 # TASK 4:Create a firewall rule that allows traffic on HTTP (tcp/80) to any address and add network tag on juice-shop
     gcloud compute firewall-rules create http-ingress --allow=tcp:80 --source-ranges 0.0.0.0/0 --target-tags [NETWORK TAG-2] --network acme-vpc

     gcloud compute instances add-tags juice-shop --tags=[NETWORK TAG-2] --zone=us-central1-b
 < Replace network tagg 2 with HTTP network tag >
 
 # TASK 5:Create a firewall rule that allows traffic on SSH (tcp/22) from acme-mgmt-subnet network address and add network tag on juice-shop
     gcloud compute firewall-rules create internal-ssh-ingress --allow=tcp:22 --source-ranges 192[dot]168[dot]10[dot]0/24 --target-tags [NETWORK TAG-3] --network acme-vpc

    gcloud compute instances add-tags juice-shop --tags=[NETWORK TAG-3] --zone=us-central1-b
<Replace network 3 with SSH internal network tag and enter dot(.) where is dot eg. 192.168.10.0/24 > 


# TASK 6:SSH to bastion host via IAP and juice-shop via bastion
    ssh [Internal IP address of juice-shop]
<open bastion ssh and paste this command..>
   
  **if task6 command not working**
  
  # try this 
      gcloud compute ssh juice-shop --internal-ip
  **ENTER**
  
  **ENTER**
  
  # congratulations you have done with LAB.
  
     
