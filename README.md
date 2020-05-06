# Ansible-Demo
Demos for Ansible Use

Demos for SE Management SSP for use with customers to showcase different aspects of Ansible

# Roles
Current role in requirements.yml is for patching Linux only


# Website
Contains formatting for web install

# Templates
add_motd
>adds a custom MOTD to the server

elasticsearch.yml.j2
>Elasticsearch configuration file for use with ELKBuild.yml

logstash.conf
>Logstash configuration file for use with ELKBuild.yml

terraform.tf.j2
>terraform main.tf for use with terraform create.yml Allows you to specify name of VM at runtime

# Playbooks
addsudouser.yml
>Add user to sudo and ensure includedir is in sudoers file

Database Install.yml
>Install latest version of mysql

ELKBuild.yml
>Build full ELK stack including Kibana. Kibana web address will be viewable at the IP address:5601

Email.yml
>Send email to variable {{ to_email }}. E-mail host information stored in Ansible Tower credentials. Depends on set_facts for {{ email_ip_address }} in order to e-mail weblink for created web site

initialconfig.yml
>Copies SSH key, Installs Katello RPM, Registers to Satellite, enables repos, installs preferred software, adds motd

linuxpatching.yml
>Using Linux patching role to patch all hosts

osprint.yml
>Prints the inventory hostname and operating system

packageupdate.yml
>Allows you to install or uninstall any package. Variable {{ package }} and {{ state }} must be filled in

rhv_vm_create.yml
>Create a VM on RHV. All ovirt_auth information stored as a credential in Ansible Tower, {{ vm_name }} and {{ vm_state }} must be supplied by user

rhv_vm_remove.yml
>Remove a VM on RHV. All ovirt_auth information stored as a credential in Ansible Tower, {{ vm_name }} must be supplied by user

ServiceNowticket Updating.yml
> Update an incident ticket in servicenow. User must supply {{ ticket_number }} and {{ state }}. {{ state }} is based on state information contained in service now and should be a number

ServiceNowticket.yml
> Create an incident ticket in servicenow. User must supply {{ incident_description }}, {{ sn_urgency }}, and {{ sn_impact }}. Ansible facts need to be gathered to pull operating system and ip_address information for ticket addition (need custom fields in ServiceNow)

terraform create.yml
>Create or remove a VM on RHV using Terraform. {{ vm_name }} must be supplied by the user. This will update the main.yml file to have a name supplied at time of fun.

wait.yml
>wait 180 seconds. This is used following a VM create in RHV to allow the agent to be installed so an IP address can be generated

Web Install and Verification.yml
> Opens firewall ports for apache and SSL, installs apache, inserts HTML5 formatting from website folder in git, inserts index page, verifies name "Alex Dworjan" exists in the content of the page, prints the web address to the screen, sets a stat for email_ip_address for use in email playbook
