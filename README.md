# Ansible-Demo
Demos for Ansible Use

Demos for SE Management SSP for use with customers to showcase different aspects of Ansible

# Roles
Current role in requirements.yml is for patching Linux only

# Templates
add_motd
>adds a custom MOTD to the server
elasticsearch.yml.j2
>Elasticsearch configuration file for use with ELKBuild.yml
logstash.conf
>Logstash configuration file for use with ELKBuild.yml
terraform.tf.j2
>terraform main.tf for use with terraform create.yml Allows you to specify name of VM at runtime

#Playbooks
addsudouser
>Add user to sudo and ensure includedir is in sudoers file
Database Install
>Install latest version of mysql
ELKBuild
>Build full ELK stack including Kibana. Kibana web address will be viewable at the IP address:5601
Email
>Send email to variable {{ to_email }}. E-mail host information stored in Ansible Tower credentials. Depends on set_facts for {{ email_ip_address }} in order to e-mail weblink for created web site
Initial Config
>Copies SSH key, Installs Katello RPM, Registers to Satellite, enables repos, installs preferred software, adds motd
Linux Patching
>Using Linux patching role to patch all hosts
osprint
>Prints the inventory hostname and operating system
packageupdate
>Allows you to install or uninstall any package. Variable {{ package }} and {{ state }} must be filled in
rhv_vm_create
>Create a VM on RHV. All ovirt_auth information stored as a credential in Ansible Tower, {{ vm_name }} and {{ vm_state }} must be supplied by user
rhv_vm_remove
>Remove a VM on RHV. All ovirt_auth information stored as a credential in Ansible Tower, {{ vm_name }} must be supplied by user
ServiceNowticket Updating
> Update an incident ticket in servicenow. User must supply {{ ticket_number }} and {{ state }}. {{ state }} is based on state information contained in service now and should be a number
ServiceNowticket
> Create an incident ticket in servicenow. User must supply {{ incident_description }}, {{ sn_urgency }}, and {{ sn_impact }}. Ansible facts need to be gathered to pull operating system and ip_address information for ticket addition (need custom fields in ServiceNow)
terraform create
>Create or remove a VM on RHV using Terraform. {{ vm_name }} must be supplied by the user. This will update the main.yml file to have a name supplied at time of fun.
wait
>wait 180 seconds. This is used following a VM create in RHV to allow the agent to be installed so an IP address can be generated
Web Install and Verification
> Opens firewall ports for apache and SSL, installs apache, inserts HTML5 formatting, inserts index page, verifies name "Alex Dworjan" exists in the content of the page, prints the web address to the screen, sets a stat for email_ip_address for use in email playbook
