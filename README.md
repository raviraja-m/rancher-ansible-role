## Launch AWS Instances:
→ git clone https://github.com/raviraja-m/rancher-ansible-role
→ $ cd rancher-ansible-role

Create the .ssh directory in user’s home directory on which you are working with(Ex: if ubuntu user create $ mkdir -p ~/.ssh)

Install python pip to install python packages

Install boto package as $ pip install boto

Execute $ yum install libselinux-python

Create Environment Variables as
export AWS_ACCESS_KEY=<aws_accesskey>
export AWS_SECRET_KEY=<aws_secretkey>

Open the rancher.yml in your favorite editor. Modify the num_nodes to the value you want. 
This number denotes the number of rancher worker nodes to be launched. 
By default one rancher server node launched and inventory file is updated with the master and worker nodes with the ip’s.
Can modify the remaining variables of your wish

→ $ ansible-playbook rancher.yml
After running this command inventory file will be updated with the newly created master and workers ip’s with ssh keys. Please check the inventory file after this

→ $ ansible-playbook ranchermaster.yml
If any error with ssh connection wait for 2 mins and proceed(Instance has to launch properly in the aws). After running this command rancher master will be launched as a container in the master node. You can browse the rancher UI by http://masterip:8080( check the ip in inventory file). 

Get rancher agent launch script from custom host launch and paste the content in raw variable in rancherworkers.yml

→ $ ansible-playbook rancherworkers.yml
This command will launch the workers
