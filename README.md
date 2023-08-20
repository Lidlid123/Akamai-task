# Akamai-task

First step:

ansible-playbook -i inventory nginx.yml
Copy
Then:

ansible-playbook -i inventory monitoring.yml
Copy
Next, in order to automate the monitoring via Ansible playbooks, I’m creating a cron job that will sample the server (nginx) every 1 minute:

* * * * * ansible-playbook -i /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/inventory /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/monitoring.yml
Copy
For testing if the logs file is populated, I created a scenario in which the webpage is not reachable:

systemctl stop nginx
Copy
For the disk space scenario:

fallocate -l 1G /tmp/large_file
Copy
For the memory scenario:

stress --vm-bytes $(awk '/MemAvailable/{printf "%d\n", $2 * 0.99;}' < /proc/meminfo)k --vm-keep -m 1

