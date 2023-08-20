# Akamai-task


For this task, I deployed 2 EC2 instances. One will act as the Ansible controller (ansible-control-node - 54.156.105.197) and the second will be the web server (webserver-Akamai - 3.216.72.120 / 172.31.15.146 (nginx server)).

I installed Ansible on the controller, then deployed nginx via the nginx.yml playbook and the monitoring script via the monitoring.yml playbook.

The steps summary is down below.

Good day! 😊




First step:

ansible-playbook -i inventory nginx.yml


Then:
ansible-playbook -i inventory monitoring.yml

Next, in order to automate the monitoring via Ansible playbooks, I’m creating a cron job that will sample the server (nginx) every 1 minute:

* * * * * ansible-playbook -i /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/inventory /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/monitoring.yml


For testing if the logs file is populated, I created a scenario in which the webpage is not reachable:
systemctl stop nginx

For the disk space scenario:

fallocate -l 1G /tmp/large_file


For the memory scenario:

stress --vm-bytes $(awk '/MemAvailable/{printf "%d\n", $2 * 0.99;}' < /proc/meminfo)k --vm-keep -m 1

