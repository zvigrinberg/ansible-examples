# Print live output of shell script task that was invoked asynchronously 


## Prerequisites

- Need the following ansible.cfg in directory of playbook, in order to use selective stdout callback plugin, so only the lines of output will be printed in the playbook.
```properties
[defaults]
# callbacks_enabled= [community.general.selective, ansible.posix.profile_tasks,ansible.posix.timer]
callbacks_enabled= [community.general.selective, ansible.posix.profile_tasks]
stdout_callback=selective
# callbacks_enabled= ansible.posix.profile_tasks
```

## Procedure

1. Invoke the playbook
```shell
ansible-playbook playbook.yaml
```
Output:
```shell
........
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  Start Of Script  ---------------------------
......
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  about to start  ----------------------------
......................................................................................................................................................................
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  Middle of Script  --------------------------
......
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  in the middle  -----------------------------
......
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  in the middle 2  ---------------------------
......
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  in the middle 3  ---------------------------
..................................................................
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  3 stage of  Script  ------------------------
......
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  3 stage of  Script 2  ----------------------
......
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  3 stage of  Script 3  ----------------------
........................................................................................................................................
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  4 stage of  Script  ------------------------
.....................................................................................................
# print next line from script output **************************************************************************************
  * localhost                  - changed=False --  final stage of  Script  --------------------
.................

# STATS *******************************************************************************************************************
localhost    : ok=541   changed=105     failed=0        unreachable=0   rescued=0       ignored=0
[zgrinber@zgrinber print-async-shell-task-live]$ 
```
