# Akamai-task

first step :
ansible-playbook -i inventory nginx.yml

then:
ansible-playbook -i inventory monitoring.yml


next in order to automate the monitoring via ansible playbooks im creating a cron job that will sample the server (nginx )
every 1 minute :

* * * * * ansible-playbook -i /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/inventory /home/ubuntu/akamai-task/Akamai-task/akamai-technical-challenge/monitoring.yml



