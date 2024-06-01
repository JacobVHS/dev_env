# MacOS Development Environment Configuration Management

## Use Case
Purpose of this playbook is to install packages, programs and configurations needed for my development workflow via Pip, homebrew and shell. Sudo elevation is only required for adding to /usr/local/bin whereas brew and pip should remain on the user level.

Prepares the following:
- Ansible
- Python Packages
- Fonts
- VS Code and custom config
- TMUX Configuration 
- Bash configuration

## Example output
```shell
$ ansible-playbook dev-environment-deploy.yml 
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'
Enter your username: jacobschreuder

PLAY [Deploy and config manage my default development environment on MacOS] ********************************************************************

TASK [Gathering Facts] *************************************************************************************************************************
ok: [localhost]

TASK [OS Homebrew | Install homebrew packages] *************************************************************************************************
ok: [localhost]

TASK [OS Homebrew | Install casks] *************************************************************************************************************
ok: [localhost]

TASK [Ansible | Install required pip packages] *************************************************************************************************
ok: [localhost]

TASK [Fonts | Create a directory if it does not exist] *****************************************************************************************
ok: [localhost]

TASK [Fonts | Change file ownership, group and permissions] ************************************************************************************
ok: [localhost]

TASK [Fonts | Download Nerdfonts CascadiaCode] *************************************************************************************************
ok: [localhost]

TASK [Fonts | Unarchive a file that is already on the remote machine] **************************************************************************
ok: [localhost]

TASK [Shell | Collect pfetch] ******************************************************************************************************************
changed: [localhost]

TASK [Shell | Install pfetch] ******************************************************************************************************************
changed: [localhost]

TASK [Shell | Collect the git status prompt shell script] **************************************************************************************
ok: [localhost]

TASK [Shell | Push out bashrc template] ********************************************************************************************************
ok: [localhost]

TASK [Shell | Push out tmux.conf template] *****************************************************************************************************
ok: [localhost]

TASK [BAT | Add catppuccin mocha theme] ********************************************************************************************************
changed: [localhost]

TASK [BAT | Add catppuccin mocha theme] ********************************************************************************************************
changed: [localhost]

TASK [BAT | Re-cache BAT] **********************************************************************************************************************
changed: [localhost]

TASK [Neovim | Clone NvChad starter config if it doesn't exist] ********************************************************************************
ok: [localhost]

TASK [Neovim | Git clone NvChad starter config] ************************************************************************************************
ok: [localhost]

PLAY RECAP *************************************************************************************************************************************
localhost                  : ok=18   changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```
