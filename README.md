# Akamai-task

first step :
ansible-playbook -i inventory nginx.yml

then:
ansible-playbook -i inventory monitoring.yml


next in order to automate the monitoring via ansible playbooks im creating a cron job that will sample the server (nginx )
every 1 minute :

* * * * * ansible-playbook -i /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/inventory /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/monitoring.yml




for testing if the logs file is populated i created a scenerio in which the webpage is not reachable : 
systemctl stop nginx

for the disk space scenerio:

fallocate -l 1G /tmp/large_file


for the memory scenerio : 

stress --vm-bytes $(awk '/MemAvailable/{printf "%d\n", $2 * 0.99;}' < /proc/meminfo)k --vm-keep -m 1


