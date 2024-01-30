<h1>Ansible Automation Lab</h1>


<h2>Description</h2>
In this lab, I will be working with Ansible to create a playbook that configures internet services on a Linux system.
<br />


<h2>Utilities Used</h2>

- <b>Shell</b>
- <b>Ansible</b>
- <b>YAML</b>
- <b>VIM text editor</b>

<h2>Environments Used </h2>

- <b>Red Hat Enterprise Linux 9</b> 
- <b>VMware</b>

<h2>Project walk-through:</h2>

<p align="center">
I changed into the designated directory and created a new Ansible playbook named internet.yml using the following commands: <br/>
<img src="https://i.imgur.com/4Kk5PwW.png"/>
<br />
<br />
Inside the internet.yml file, I added entries to start the first play named "Enable internet services." I specified the managed host as serverb.lab.example.com, enabled privilege escalation, and added entries to the playbook to define a task that installs the latest versions of required packages:  <br/>
<img src="https://i.imgur.com/5rRx0Ad.png"/>
<br />
<br />
I defined entries to configure the firewalld, ensuring that the firewalld service is enabled, running, and that access is allowed to the http service.: <br/>
<img src="https://i.imgur.com/nAKifl8.png"/>
<br />
<br />
I added entries to ensure that the httpd and mariadb services are enabled and running.: <br/>
<img src="https://i.imgur.com/zdqDy00.png"/>
<br />
<br />
I used the ansible.builtin.copy module to copy the index.php file to the /var/www/html/ directory on the managed host. The file mode was set to 0644: <br/>
<img src="https://i.imgur.com/7Ji6csB.png"/>
<br />
<br />
I added another play to the playbook for a task to be performed on the control node. This play tests access to the web server running on serverb.lab.example.com without requiring privilege escalation. It runs on the workstation.lab.example.com managed host. Inside the new play, I added an entry using the ansible.builtin.uri module to test the web service running on serverb from the control node, looking for a return status code of 200.: <br/>
<img src="https://i.imgur.com/VmBAQlh.png"/>
<br />
<br />
I validated the syntax of the internet.yml playbook using the following command: <br/>
<img src="https://i.imgur.com/df2Pogu.png"/>
<br />
<br />
I executed the ansible-navigator run command in the terminal to initiate the playbook execution and from the results we can see that there were no failures: <br/>
<img src="https://i.imgur.com/64EPVMH.png"/>
