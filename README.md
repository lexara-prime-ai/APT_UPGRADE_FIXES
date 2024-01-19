## Question
* How to check "apt-get upgrade" status after losing ssh connection?

### Answer

*  I had an upgrade in progress (asking me whether to keep or replace a config file; this information I took from `/var/log/apt/term.log` when my terminal was closed by another person. Restarting apt upgrade complained about a lock file being held.

* My fix was to do the following:

```bash
sudo killall apt # to release the lock
sudo dpkg --configure -a # to fix the interrupted upgrade
sudo apt upgrade # to make sure no packages are left not upgraded
```
