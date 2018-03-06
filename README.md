# ANSIBLE_COMMANDS

# ad hoc commands
Now, here we are using another module called ‘command‘, which is used to execute list of commands (like, df, free, uptime, etc.) 
on all selected remote hosts at one go, for example watch out few examples shown below.

# To check the partitions on all remote hosts
 ansible -m command -a "df -h" web-servers

#  Check memory usage on all remote hosts.
 ansible -m command -a "free -mt" web-servers

#  Checking Uptime for all 3 servers.
 ansible -m command -a "uptime" web-servers

# Check for hostname and Architecture.

 ansible -m command -a "arch" web-servers
 ansible -m shell -a "hostname" web-servers

#  If we need the output to any file we can redirect as below.
  ansible -m command -a "df -h" web-servers > /tmp/df_outpur.txt

# Manually flushing controller's redis cache
ansible localhost -m redis -a "command=flush flush_mode=all" -c local

# Limit to one or more hosts
 This is required when one wants to run a playbook against a host group, but only against one or more members of that group.
ansible-playbook playbooks/PLAYBOOK_NAME.yml --limit "host1"

# Limit to multiple hosts
ansible-playbook playbooks/PLAYBOOK_NAME.yml --limit "host1,host2"
Negated limit. NOTE: Single quotes MUST be used to prevent bash interpolation.

ansible-playbook playbooks/PLAYBOOK_NAME.yml --limit 'all:!host1'
# Limit to host group
ansible-playbook playbooks/PLAYBOOK_NAME.yml --limit 'group1'

# Limiting Tasks with Tags
Limit to all tags matching install
ansible-playbook playbooks/PLAYBOOK_NAME.yml --tags 'install'

# Skip any tag matching sudoers
ansible-playbook playbooks/PLAYBOOK_NAME.yml --skip-tags 'sudoers'
