# EBS
## WORKING WITH EBS
## NAME: Dhanalakshmi C
## REG NO: 212225230050
## Aim
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

## Algorithm / Steps
Create a new Amazon EBS volume with a size of 1 GiB.

Select the same Availability Zone as the EC2 instance.

Attach the EBS volume to the EC2 instance using /dev/sdb.

Connect to the EC2 instance using AWS Systems Manager Session Manager.

Check the available storage using df -h.

Create an ext3 file system on the EBS volume.

Create the /mnt/data-store directory.

Mount the EBS volume to /mnt/data-store.

Configure /etc/fstab for automatic mounting.

Verify that the EBS volume is successfully mounted.

Create file.txt inside the mounted EBS volume.

Verify the contents of the created file.

Create an EBS snapshot named My Snapshot.

Delete file.txt from the original EBS volume.

Create a new EBS volume from the snapshot.

Attach the restored volume to the EC2 instance using /dev/sdc.

Create the /mnt/data-store2 directory.

Mount the restored volume to /mnt/data-store2.

Verify that file.txt has been successfully restored.

## Program
## 1. Check Available Storage
```
df -h
```
## 2. Create an ext3 File System
```
sudo mkfs -t ext3 /dev/sdb
```
## 3. Create a Mount Directory
```
sudo mkdir /mnt/data-store
```
## 4. Mount the EBS Volume
```
sudo mount /dev/sdb /mnt/data-store
```
## 5. Configure Automatic Mounting
```
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```
## 6. View the File System Configuration
```
cat /etc/fstab
```
## 7. Verify the Mounted Volume
```
df -h
```
## 8. Create a File in the EBS Volume
```
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```
## 9. Read the File
```
cat /mnt/data-store/file.txt
```
## 10. Delete the File
```
sudo rm /mnt/data-store/file.txt
```
## 11. Verify File Deletion
```
ls /mnt/data-store/
```
## 12. Create a Mount Directory for the Restored Volume
```
sudo mkdir /mnt/data-store2
```
## 13. Mount the Restored EBS Volume
```
sudo mount /dev/sdc /mnt/data-store2
```
## 14. Verify Snapshot Restoration
```
ls /mnt/data-store2/
```
## Expected output:
```
file.txt
```
<img width="1917" height="1078" alt="Screenshot 2026-11-18 150539" src="https://github.com/user-attachments/assets/199a4387-8f4a-4915-a549-250216afdecf" />
<img width="1917" height="1078" alt="Screenshot 2026-11-18 150723" src="https://github.com/user-attachments/assets/628dae91-2ed5-471a-80e5-44f9d4c13f50" />
<img width="1908" height="1071" alt="Screenshot 2026-11-18 150847" src="https://github.com/user-attachments/assets/7ae75009-e6fb-4efd-a243-4aca538fa2dc" />
 
<img width="1912" height="1078" alt="Screenshot 2026-11-18 151148" src="https://github.com/user-attachments/assets/a8e6caac-704d-40a5-a44a-53e23451ba59" />
<img width="1917" height="1075" alt="Screenshot 2026-11-18 151202" src="https://github.com/user-attachments/assets/9abbde08-21a5-4fa2-8d08-673ca4539f40" />
<img width="1917" height="1067" alt="Screenshot 2026-11-18 151819" src="https://github.com/user-attachments/assets/38a37a7b-8064-400e-b622-ca7d7ef42939" />
<img width="1485" height="185" alt="Screenshot 2026-11-18 151844" src="https://github.com/user-attachments/assets/c858300f-7a6e-41f6-a4a9-e508418008f9" />
<img width="1917" height="1075" alt="Screenshot 2026-11-18 152131" src="https://github.com/user-attachments/assets/39f927bc-67a2-467c-873a-99c299cb222f" />
<img width="1917" height="1073" alt="Screenshot 2026-11-18 152301" src="https://github.com/user-attachments/assets/1ed07a45-a77a-405c-9ec6-88763f735e9e" />
<img width="1917" height="1078" alt="Screenshot 2026-11-18 152619" src="https://github.com/user-attachments/assets/428cedc0-5ddd-46cf-b662-e169fac4919e" />
<img width="1917" height="1072" alt="Screenshot 2026-11-18 152802" src="https://github.com/user-attachments/assets/61f34dd9-b15f-48c2-8716-53e6e95f5f3b" />
<img width="1916" height="1077" alt="image" src="https://github.com/user-attachments/assets/f8c7c4ad-96aa-4364-96b7-bfeeeee728be" />

## Result
Thus, an Amazon EBS volume was successfully created, attached and mounted to an EC2 instance. A snapshot backup was created and restored to a new EBS volume.
