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

Manually flushing controller's redis cache
ansible localhost -m redis -a "command=flush flush_mode=all" -c local
