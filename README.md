ssh-agent on Bash on Ubuntu on Windows
======================================

Scripts to use to persist `ssh-agent` on WSL + Ubuntu


Install
-------
1. Open Windows bash (WSL)
2. Put the scripts into place
```
mkdir -p ~/local/bin
cp -vf ./start-ssh-agent ~/local/bin
```
3. Open Task Scheduler and create a scheduled task (optionally in a directory `MyTasks`) to execute this command at login
```
powershell -NoProfile -WindowStyle Hidden -Command C:\Windows\System32\bash.exe -c start-ssh-agent
```
4. After the task is created, open the task properties and under conditions, uncheck power options.
5. Finally, open Bash, and edit your `.bashrc` to include the following:
```
# Append ~/local/bin to PATH
# Useful for installing binaries from source
export PATH="$PATH:$HOME/local/bin"

# Make shell aware of SSH_AGENT_PID and SSH_AUTH_SOCK variables
# so that processes can communicate with ssh-agent
. ~/.ssh/environment > /dev/null
```

Original Author
---------------
[Dave Eddy](http://daveeddy.com/2017/10/18/persistent-sshagent-on-bash-on-ubuntu-on-windows/)

License
-------

MIT License
