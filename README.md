---

# Openshift installation 60 days trial

This project explains how to install an Openshift Cluster in a vCenter/vMware environment

## Prerequisites

- Ensure the Network that you will use has DHCP enabled.
- Access to the internet for downloading necessary packages and configuring the cluster

## Installation Steps

Follow the steps below to install create the cluster

### 1. Create an account in red hat https://console.redhat.com/
You need to create an account in Red Hat so you could create the cluster 
![image](https://github.com/user-attachments/assets/d52e23c2-ccd9-4473-821a-42b5ab58f897)


### 2. Login in your account and select create cluster

Once you logged in your account go to Red Hat openshift service:
![image](https://github.com/user-attachments/assets/e0233961-37e0-4a13-a509-6f7020d85293)
Select clusters and create cluster:
![image](https://github.com/user-attachments/assets/39d90ce0-af73-44d6-9880-317813eb6972)
You will need to select datacenter and assist installation:
![image](https://github.com/user-attachments/assets/0a295f48-6e34-4585-881a-e830382cf187)


### 3. Configure Cluster details

Add the cluster details(it is not required to add a public domain but you might need to add the records in your computer):
![image](https://github.com/user-attachments/assets/ea5844d0-446d-47eb-ad5c-37364b0a6888)

### 4. Keep the defaults under operators

![image](https://github.com/user-attachments/assets/7bc9899a-6702-4145-aa3a-748862837daa)

### 5. Under host discovery please create the ISO that will be use to install the OS
## Note: Please make sure to create the ssh key with keygen so you can login to your servers.
![image](https://github.com/user-attachments/assets/a1d61bb2-7a9e-4085-aad1-0531671f2ffa)
### 6. Download the generated ISO to install it in vMware.
### 7. Login in the vCenter
### 8. Upload the ISO in the vCenter
![image](https://github.com/user-attachments/assets/6f0a67dc-8bbc-444e-a3de-87c67a1098f7)
### 9. Create the 3 machines with the minimum required.
## Important points
1. Select guest OS it is Red Hat Linux
<img width="488" alt="image" src="https://github.com/user-attachments/assets/0a0f338d-6cce-4f00-935a-011a53b232b0">

2. CPU virtualization should be enabled:
<img width="477" alt="image" src="https://github.com/user-attachments/assets/67e70134-ef56-4ab4-b907-f152cb5d4236">

3. ISO need to be selected and check connect at power on:
<img width="350" alt="image" src="https://github.com/user-attachments/assets/634ef201-2663-495f-aa16-96250722e035">

4. Under Advanced Paramaters you need to add the following disk.EnableUUID as true:
<img width="503" alt="image" src="https://github.com/user-attachments/assets/72eb37d4-8a05-4752-9980-1a80c2a34055">

### 10. Boot the computers and wait until they show up in the Red Hat Console, you can press next after that.
### 11. Follow the last steps with the defaults and press create cluster.
### 12. Once created you can get the DNS configuration that is required and also the user and password for your cluster:
<img width="649" alt="image" src="https://github.com/user-attachments/assets/6c02ac97-dda6-4cba-814e-a1c5f774804f">


## Notes

- The first time you try to upload the ISO it might fail, please make sure to read the error, open the URL that is failing, trust the certificate and upload the file again.
- Verify that all nodes can reach red hat url to create the cluster
- Make sure you have modified the disk to have uuid enabled.

For further details on Ansible and Kubernetes, refer to their official documentation:

- [Openshift documentation][[(https://docs.ansible.com/](https://docs.openshift.com/container-platform/4.10/installing/index.html))]

## Troubleshooting

If you encounter issues during the setup, consider checking the following:

- Verify the network connectivity to internet
- Verify you have added the minimal resources required 
- Make sure you have modified the disk to have uuid enabled.

## Contributing

Contributions are welcome! Feel free to fork the repository and submit pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
