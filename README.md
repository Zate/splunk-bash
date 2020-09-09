# splunk-bash
As a Splunk Sales Engineer I needed a way to quickly build and tear down Splunk instances for creating demos and testing out scenarios. Since I'm also a lasy admin, I wanted a way to do this in a simple and repeatable fashion. What I built was a series of simple commands that live in your `$HOME/.profile` which allow you to do a host of functions. 

For users in ZSH, you'll need to update your `$HOME/.zprofile` with the commands. 

## Install Process

1. Download Splunk (splunk-<version>-<build>-<os>.tgz) from www.splunk.com. * Make sure to get the *.tgz file. * Install it in your /opt/upgrade directory: `tar xzvf splunk-<version>-<build>-<os>.tgz -C /opt/upgrade` This will put the splunk bits in the Splunk Upgrade (`/opt/upgrade/splunk`) Directory
  
2. Get your developer license from [Splunk Dev](dev.splunk.com) dev.splunk.com and put it in your downloads directory.

### Install 

Run this command:
`curl -Ssl https://s3.amazonaws.com/splunk-bash-installs/install.sh | bash`

This will download and install the bash file in this git repo and add it to your local $HOME/.profile . Once it's done, restart your terminal session.

### Install EventGen

I've added the shell script `install_eventgen.sh` to the package which just runs the following commands and installs eventgen on your splunk instance: 

`wget https://s3.amazonaws.com/splunk-bash-installs/install_eventgen.sh 
sh install_eventgen.sh`

Once installed, you can add any TA (that is eventgen enabled) and start seeing sample data flow into your instance.

## Commands

- createsplunk 
  - creates a local instance of Splunk by copying bits from local repository. 
  - usage: `createsplunk <instance_name>`  
- startsplunk   
  - starts splunk instance
  - usage: `startsplunk <instance_name>`
- stopsplunk
  - stops splunk instance
  - usage: `stopsplunk <instance_name>`
- cds
  - changes directory into splunk instance
  - usage: `cds <instance_name>`
- addlic
  - adds a license to local splunk instance
  - usage: `addlic <instance_name>`
- splunkspace
  - displays the total space used by splunk instance
  - usage: `splunkspace <instance_name>`
- backupsplunk
  - backs up (/etc/apps directory) from splunk instance
  - usage: `backusplunk <instance_name>`
- restoresplunk
  - restores splunk instance (/etc/apps directory only)
  - usage: `restoresplunk <old_instance_name> <new_instance_name>`
- listapps
  - lists apps from the local splunk instance
  - usage: `listapps <instance_name>`
- fixperm
  - fixes permissions with splunk instance
  - usage: `fixperm <instance_name>`
- upgradesplunk
  - upgrades the local splunk instance
  - usage: `upgradesplunk <instance_name>`
- cleansplunk
  - cleans splunk instance
  - usage: `cleansplunk <instance_name>`
- rmsplunk
  - removes splunk instance
  - usage: `rmsplunk <instance_name>`
- svm
  - parent command that can run some sub-commands
    - list
      - usage : svm list
      - shows list of installed splunk instances with their versions
    - running
      - usage : svm running
      - shows running instances
                
### Directory Structure

- SPLUNK_HOME = /opt/splunk
- SPLUNK_LIC = ~/Downloads
- BASE_DIR = /opt/splunk
                        
- Splunk Subdirectories 
  - /opt/splunk/splunk_test
  - /opt/splunk/splunk_test2
  - /opt/splunk/splunk_testN

  
                
