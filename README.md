Linux Hardening

<h1> Linux Security Hardening </h1>


<h2>Project</h2>

This project is to demonstrate basic security hardening steps on a Linux virtual machine (VM) to secure the system. The goal is to showcase fundamental skills in configuring a Linux environment for improved security.


<h2>Prerequisites<h2>

- <b>A Linux distribution installed on a Virtual Machine (I will be using Ubuntu).</b>
- <b>Basic knowledge of Linux commands and access to the root user or sudo privileges.</b>


<h2>Walk-through</h2>

Step 1: Setting Up the Linux VM

- Install your preferred Linux distribution on a virtual machine of your choice.
- Create a new user account instead of using the root account directly.
   ![2](https://github.com/user-attachments/assets/5e139cd3-f161-44c5-811a-935f98e33626)
   ![3](https://github.com/user-attachments/assets/7bb80351-b5a4-418f-8ad3-c1aeaba37f05)


Step 2: Update the System

 - Before starting any configuration, update the package list and upgrade installed packages. Run 'sudo apt update' & 'sudo apt upgrade'.
   ![4](https://github.com/user-attachments/assets/f9e34b0d-f472-4c27-aab5-a21de2ce10ee)
   ![5](https://github.com/user-attachments/assets/57fa94e9-8c98-414f-929d-c2f90e0f8108)


Step 3: Configure the Firewall (UFW)
- Check if UFW (Uncomplicated Firewall) is installed. If not, install it with this command "sudo apt install ufw".
  ![6](https://github.com/user-attachments/assets/c2b8b4c6-e83b-474f-88a5-7680f30b2c1d)


- Enable UFW and set default rules by running these commands one at a time:
   'sudo ufw default deny incoming' then 'sudo ufw default allow outgoing'
   ![7](https://github.com/user-attachments/assets/930a55a7-f913-45ae-9bf7-bee78f4e758e)
   ![8](https://github.com/user-attachments/assets/41384c67-b5ba-4c06-81ab-05cf35a9b87d)


- Allow specific services. I will allow SSH, HTTP, & HTTPS by running these commands:
   'sudo ufw allow ssh', 'sudo ufw allow http', 'sudo ufw allow https'
    ![9](https://github.com/user-attachments/assets/e4064407-1b87-4521-bf7c-352905fd31dd)


- Enable the firewall: Run 'sudo ufw enable' to enable the firewall.  
  ![10](https://github.com/user-attachments/assets/5897bccc-76c7-4392-b84c-38773e3b3e3e)


Step 4: Disable Unused Services

- List all services running at startup. Run 'sudo systemctl list-unit-files --type=service' and press Enter.
  ![11](https://github.com/user-attachments/assets/6654dff8-ee2f-4a59-9f08-a572ab652a2a)

- Identify and disable unnecessary services if. Run 'sudo systemctl disable [service_name]'. and press Enter. 
  

Step 5: Set Up User Access Control

- Create strong passwords for all user accounts: Run 'sudo passwd [username]' then press Enter.
  ![12](https://github.com/user-attachments/assets/53110c39-c998-4d74-b1c6-b172fe222022)

  
- Limit SSH access to specific users by editing the SSH config file: Run 'sudo nano /etc/ssh/sshd_config' to open the file.
  Now add the following line: 'AllowUsers [specific_username]'
  ![13](https://github.com/user-attachments/assets/7502c909-28d5-42fe-9303-0941220551ed)

- Restart the SSH service by running 'sudo systemctl restart ssh'
  ![14](https://github.com/user-attachments/assets/b4a4d1fa-0951-4b2d-8b6f-00fa129f553c)


Step 6: Enable Automatic Security Updates.
- Install unattended upgrades to enable automatic security updates: Run 'sudo apt install unattended-upgrades'.
  ![15](https://github.com/user-attachments/assets/78ac068c-1009-4f26-a284-a651a0dd04a7)

- Configure it by running 'sudo dpkg-reconfigure unattended-upgrades'
  ![16](https://github.com/user-attachments/assets/1c1ded93-903f-4bfe-a5af-523f12a5a330)


Step 7: Log Monitoring
- Use the journalctl command to check system logs: For example run 'journalctl -p 3 -xb'
  ![17](https://github.com/user-attachments/assets/129fc735-92c7-43a6-a8cd-bc2424fb972f)

- Monitor login attempts with command 'sudo cat /var/log/auth.log'
  ![18](https://github.com/user-attachments/assets/dd58c0fd-9c4e-46cb-a1bd-1a1530771e3e)

