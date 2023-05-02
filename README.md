# Steps taken to configuring the Pi-Stack

1. Install Ansible on your local machines
2. Clone the Ansible Playbook repository: git clone https://github.com/rancher/k3s-ansible.git
3. Installing the command line tool for ansible-playbook. sudo apt install ansible-core -y 
4. Make the directory for the Ansible config file separate from the sample files:
    mkdir -p /home/pi/k3s-ansible/inventory/prod

4. Copy the sample file to the new directory: 
    cp -r /home/pi/k3s-ansible/inventory/sample/hosts.ini /home/pi/k3s-ansible/inventory/prod/

5. Configure your inventory file with the ip addresses. See the Example Below
<Insert the host.ini file here>

6. Now, securely copy this file to other nodes, while creating the new directory destination.
     scp -r hosts.ini <hostname>@<ip-address>:/home/<name>

7. Login to the server you secure copied the files too.
    a. sudo su
    b. mkdir -p /home/pi/k3s-ansible/inventory/prod
    c. mv /home/pi/hosts.ini /home/pi/k3s-ansible/inventory/prod
    d. cat /home/pi/k3s-ansible/inventory/prod/hosts.ini (For verification)

8. Run the Ansible playbook: 
    ansible-playbook -i k3s-ansible/inventory/prod/hosts.ini k3s-ansible/site.yml