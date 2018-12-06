# my-demo

A. On Ansible server:

1. Install ansible on ubuntu 14.04:

   cmd: sudo apt-get install ansible 

   This cmd will create hosts, ansible.cfg files at /etc/ansible path.

   To disable host checking modify ansible.cfg and put "host_key_checking = False" inside [defaults]

   Edit hosts file and put the provided server ip.

   This hosts file acts as inventory file.


2. Generate ssh keypair on server A.

   cmd: ssh-keygen

   This will create public and private key file.

   Now we need to copy public key onto provided server within authorised file with the following cmd:

   ssh-copy-id -i ~/.ssh/id_rsa.pub ubuntu@publicip_of_host

   This cmd will ask for entering the password for the user, enter the provided password for user ubuntu.

   Now the public key has been successfully added on remote node.


3. Check the connection between ansible server and the node by following cmd;

    ansible all -m ping -u --ask-pass

    after hitting the cmd enter the password of remote node.

    now the result will display as "pong" for ping request, that means connection is successfull.

4. Running playbook on ansible server:

   following is the cmd to run the playbook:

   sudo ansible-playbook setup.yml --ask-pass

   Enter the password when prompted.


Playbook details:

 The playbook setup.yml creates tomcat cluster which is load balanced and which consist of two nodes.

 The playbook installs apache,mysql and tomcat(2 instances) and register there services at the system startup
  
 mod_jk is the Apache module that will be used to provide our cluster with its load balancing and proxy capabilities and uses AJP protocol



 Result:

 http://public_ip_of_node ------will navigate to tomcat default page
 http://public_ip_of_node/status-----to view status of nodes
 http://public_ip_of_node/index.jsp


 
 	







   





