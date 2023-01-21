## CLOUD DATABASE ADMINISTRATION

DigitalOcean $200 Credit for 60 Days: https://m.do.co/c/8722350423f7

### SETUP 2 VMs ON DIGITAL-OCEAN
```
1. Create New Project called `MySQL`
2. Create `Droplets`
3. Region: New York (please choose that is closer to you)
4. Choose Image: CentOS 7
5. Droplet Type: Basic
6. CPU Options: Regular(SSD) 1GB/1CPU
7. Authentication Method - SSH Key - New SSH Key `Key-Name: cloud-db`
8. Quantity: 2
9. Droplet-1 Name: primary & Droplet-2 Name: replica
10. Create
```

### DISABLE SELINUX & EDIT HOSTS FILE
```
1. Disable `selinux` on both primary & replica
2. Edit the `/etc/hosts` file to add friendly DNS name of target host
3. Reboot both Primary & Replica Server
```
