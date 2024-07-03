# DataSintesa-DevOps-Engineer-Take-home-Test

# General Knowledge Check
1.	What is your favorite Linux distro and why? 
Ubuntu is a favorite because it’s user-friendly, has strong community support, offers long-term support (LTS), has a vast software repository, is versatile for various uses, includes robust security features, is widely compatible with hardware, and follows a predictable release cycle.

2.	What do you know about Container and Virtual Machine?

- Containers provide a way to virtualize the user space of an operating system, such as Docker.

- Virtual Machines (VM), on the other hand, virtualize the entire hardware environment, including the OS, thereby allowing multiple operating systems to run simultaneously on the same physical machine.such as Ubuntu, Fedora, Debian, and CentOS.

3.	How is Container different from Virtual Machine?

Containers are generally more portable across different environments because they package applications and their dependencies together, whereas VMs encapsulate entire OS environments.

4.	How can you sync two local directories in Linux?

      To sync two local directories in Linux, you can use several methods such as rsync, cp (copy), or scp (secure copy) depending on your specific needs:

      - Using rsync: Example command: rsync -av /source/directory/ /destination/directory/
      - Using cp: Example command: cp -av /source/directory/* /destination/directory/
- Using scp: Example command: scp -r /source/directory/  user@remote_host:/destination/directory/

5.	What is swap in Linux and what is it used for?

      Definition: Swap space is a reserved area on a disk that can be used as virtual memory by the operating system when physical RAM (Random Access Memory) is full.
      Usage: It acts as an overflow area for RAM, allowing the system to temporarily move inactive memory pages from RAM to disk, thereby freeing up physical memory for active processes.
      Purpose: Swap space helps prevent out-of-memory errors and allows systems to handle more applications simultaneously than would be possible with physical RAM alone.
Configuration: Swap space can be allocated during installation or manually configured later using tools like swapon and fstab in Linux distributions.







6.	You have to find all files larger than 20 MB in your Linux OS. How you do it?

   ![1](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/dbc37222-da69-4a9f-8ad8-9bf429247fad)

             (/) specifies the starting directory for the search (root directory).
             (-type f) specifies that you are looking for files.
             (-size +20M) specifies that the file size should be greater than 20 MB.

7.	What is happening when the Linux kernel is starting the OOM killer and how does it choose which process to kill first?

              When the Linux kernel starts the Out-Of-Memory (OOM) killer, it means the 
               system is critically low on memory and must free up memory to keep running.
               Here's what happens and how the OOM killer decides which process to terminate:

              Detection: The system is low on memory.
              Activation: The kernel starts the OOM killer.
              Scoring: Processes are scored based on memory usage, user privilege, process age, 
                             and nice value.
              Termination: The process with the highest score is killed to free up memory.
 
              Example Commands for Viewing and Setting OOM Scores:
              
              To view the OOM score of a process



![6](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/f0a6d9b0-cb41-4788-a10b-5d56f16a57d7)

               
               To adjust OOM scores


![7](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/1d636014-a11f-4fd5-b8e6-acd4d7ee2b68)



8.	Explain the following command : (date ; ps -ef | awk '{print $1}'| sort | uniq | wc -l) >> Activity.log

             This command logs the current date and the number of unique users running 
             processes to a file called Activity.log.
```
   date: Prints the current date and time.
   ps -ef: Lists all running processes in full-format listing.
   awk '{print $1}': Extracts the first column from the ps output, which is the user owning the 
   process.
   sort: Sorts the list of users.
   uniq: Filters out duplicate entries, leaving only unique user names.
   wc -l: Counts the number of lines (unique users) from the sorted list.
   >> Activity.log: Appends the output to the file Activity.log.

```






9.	Server A cannot talk to Server B. Describe possible reasons!

             Network Issues: Check cables, hardware, and network configurations.
             IP Address Issues: Verify correct IP addresses and subnet configurations.
             Firewall Rules: Ensure firewalls on both servers allow traffic.
             Routing Issues: Check routing tables and default gateways.
             DNS Issues: Verify DNS resolution and hosts file configurations.
             Service Issues: Ensure necessary services are running and ports are open.
             Security Groups/ACLs: Check cloud security groups and access control lists.
             Network Segmentation: Ensure proper VLAN configurations and routing.
             Performance Issues: Check for network congestion and resource constraints.

10.	How to know which process in Linux listens on a specific port?

              To find which process is listening on a specific port, you can use the netstat, ss, or lsof 
              commands.


![2](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/236e2200-0a0d-48e3-8215-13d6a444971b)

![3](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/51f1ebff-b5c8-41c4-8350-fd4644804568)

![4](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/4383e891-e982-44a6-995c-3c5782d5e719)

               


11.	An engineer type http://www.yahoo.com in the browser and he/she presses enter. What happens next? (hint: describe activities happening at every OSI layer - physical, data link, network, transport, session, presentation, application layer)

              Application Layer (Layer 7): Browser creates an HTTP GET request.
              Presentation Layer (Layer 6): Request data is formatted for transmission.
              Session Layer (Layer 5): Session is established to maintain connection state.
              Transport Layer (Layer 4): Request is segmented into TCP packets; TCP 
              connection initiated.
              Network Layer (Layer 3): TCP segments are encapsulated in IP packets and routed 
              to Yahoo's server.
              Data Link Layer (Layer 2): IP packets are framed, MAC addresses added, and data 
              transmitted.
              Physical Layer (Layer 1): Frames are converted to electrical/optical signals and 
              sent over the physical medium.













12.	What about if the engineer change from http://www.yahoo.com into https://www.yahoo.com ? (hint : describe activities related to public/private certificates, CAs, proxying, MiTM, etc)

             Data Encryption: 
                  -Data between the client and server is encrypted using SSL/TLS.
             SSL/TLS Certificates:
                  -The server sends an SSL/TLS certificate containing its public key.
                  -This certificate is issued by a trusted Certificate Authority (CA).
             SSL/TLS Handshake:
                  -The client and server perform a handshake to verify the certificate and ‘
                  create a session key used for encryption.
             Additional Security:
                  -Using HTTPS protects data from Man-in-the-Middle (MiTM) attacks 
                  because the data is encrypted.
                  -Proxies can also use HTTPS to ensure data security.



13.	A web developer is creating a new web application and you have to store the user’s passwords in a database. How would you store the passwords securely?

              Use a strong hashing algorithm:
                  -Hash passwords using a strong, one-way hashing algorithm like bcrypt, 
                  Argon2, or PBKDF2.
                  Example: hashed_password = bcrypt.hashpw(plain_password, bcrypt.gensalt())

               Salting:
                  Add a unique, random salt to each password before hashing.
                  Store the salt along with the hashed password in the database.

               Peppering (Optional):
                  Add a server-side secret (pepper) to the password before hashing. This pepper 
                  should not be stored in the database but kept securely on the server.

              Regular updates:
                  Periodically update hashing algorithms and re-hash stored passwords using 
                  stronger algorithms if necessary.



















14.	A DevOps engineer have added a public ssh key of a developer into authorized_keys but the developer is still getting a password prompt, what can be wrong?

             File Permissions: Ensure correct permissions on .ssh and authorized_keys.

           
![7](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/44dc1e09-910a-443d-9812-c4ee88dda74b)



             SSH Key Format: Ensure the key is correctly formatted.
             SSHD Configuration: Ensure PubkeyAuthentication yes is enabled in sshd_config.
             Key Type: Ensure the key type is supported by the server.
             SSH Agent: Ensure the SSH agent is running and the key is added using ssh-add.

15.	Describe the Linux boot process with as much detail as possible, starting from when the system is powered on and ending when you get a prompt!

              BIOS/UEFI: Initialize hardware and load bootloader.
              Bootloader (GRUB/LILO): Select and load the kernel.
              Kernel Initialization: Initialize hardware and root filesystem.
              init or systemd: Start the first user-space process and system services.
              System Services: Start essential services (networking, logging).
              Runlevel/Target: System reaches the specified runlevel/target.
              Login Prompt: Display login prompt on console or GUI.
              User Login: Shell or desktop environment started after login.


# Take-Home Tests

## Overview
Your goal is to set up a simple hello-world Node.js app called oss on a development VM / container.

The code for the simple Express web server as follows :
```
// Simple Express web server
// @see http://howtonode.org/getting-started-with-express

// Load the express module
var express = require('express'); var app = express()


// Respond to requests for / with 'Hello World' app.get('/', function(req, res){
res.send('Hello world!');
});

// Listen on port 80
app.listen(80, () => console.log('Express server started successfully.'));
```

The package.json file as follows :
```
{
"name": "examplenodeapp",
"description": "Example Express Node.js app.",
"author": "dtndevopscandidate <devopscandidate@datasintesa.id>", "dependencies": {
"express": "4.x"
},
"engine": "node >= 0.10.6"
}
```

## Goals
The server should be running :

1.	Centos ≥ 7
2.	Nginx ≥ 1.15
3.	Postgresql ≥ 11 4. Node.js >= 0.10.6

The server must have 3 easily executable bash scripts in /opt/oss/bin :

1.	bin/stop → stop the Express server, nginx, and postgresql.
2.	bin/start → start the Express server, nginx, and postgresql.
3.	bin/backup → dump the postgresql database to a .sqlfile in
/opt/oss/data/backups

## Outputs
A dockerfile or a vagrantfile which fulfills all the goals listed above, along with the 3 executable bash scripts.

Submit the answer to the recruiter max 2 days after day of assignment.

## Answer


![8](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/15eb3244-0d9c-46e3-9640-d88783ca894d)

![9](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/6806acc0-eca9-4422-ac7f-83ab7d1de379)
![10](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/5a3c0268-2e6c-4b9b-8c4a-ac8747f7756e)

![11](https://github.com/jerryfernando/DataSintesa-DevOps-Engineer-Take-home-Test/assets/23428256/13642040-6e3e-4743-86af-e7319b4b07d7)

