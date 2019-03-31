# Disk Space Monitor

Small script which can be used to send notifications when a there is not enough space on disks.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them

```
sudo apt-get install swaks 
```

### Installing

Follow these instructions for setting up the Disk Space monitor

Create a directory ( choose your preferred location )

```
sudo mkdir .scripts 
```

Change permissions of the created directory

```
sudo chmod 700 .scripts
```

Download and create the Source file 

```
sudo sh -c 'curl https://raw.githubusercontent.com/4ddev/Disk-Space-Monitor/master/disk_space_monitor > .scripts/disk_space_monitor.sh'
```

Change file permissions 

```
sudo chmod 700 .scripts/disk_space_monitor.sh
```

Start the installation process - verify that you changed the directory to .scripts
This will generate a cronjob at 4AM and a logrotate configuration file also some default files in the directory will be generated 
The cronjob will be generated as root user 
```
sudo /bin/bash -c "cd .scripts; ./disk_space_monitor.sh -i"
```

Store your smtp Password to the generated Password file 

```
sudo /bin/bash -c 'echo "YOUR_PASSWORD" > .scripts/smtp_pw.txt'
```

Store a default Message in the message file 

```
sudo /bin/bash -c 'echo "YOUR MESSAGE" > .scripts/message.txt'
```


Open the file by typing 

```
sudo nano .scripts/disk_space_monitor.sh 
```

Change these parameters to your needs 

```
# PROJECT NAME this will be added to the Subject 
PROJECT_NAME="PROJECT_NAME"

# Location of your password File - dont forget to change the file permissions!
AUTH_PASSWORD="smtp_pw.txt"

# Define your disks here delimited by whitespace for example "sda sdb" 
DRIVES="/dev/root /dev/mmcblk0p1"

# Limit - when this value is reached send mail to user
ERROR_WHEN=80

# Account which will be used as relay to prevent dns lookup error
FROM="YOUR EMAIL ADDRESS"

# Account auth user
AUTH_USER="YOUR EMAIL ADDRESS LOGIN"

#SMTP RELAY SERVER 
SMTP_SERVER="SMTP SERVER"

# User which receiving the mail  - delimited by , for example "example@example.com,other@example.com"
RECIPIENTS="TARGET EMAIL"

# Message Location 
MESSAGE="message.txt" 

# The Subject of the Email 
SUBJECT="Disk space alert! Detected low memory on disk!"
```

After changing the necessary parameters all should be working well. These could be your output.

```
Fr 28. Dec 20:36:34 UTC 2018 Checked filesystem space of disk: /dev/root Remaining space: 8,0G used: 6,0G  43 size: 15G
Fr 28. Dec 20:36:34 UTC 2018 Checked filesystem space of disk: mmcblk0p1 Remaining space: 21M used: 22M  52 size: 43M
Fr 28. Dec 20:36:35 UTC 2018 exited with no error - mail successfully send
```

### Deinstall 

You are able to remove all generated files of this script with this routine 
```
sudo /bin/bash -c "cd .scripts; ./disk_space_monitor.sh -r"

or 

sudo /bin/bash -c "cd .scripts; ./disk_space_monitor.sh --deinstall"
```

## Running the tests

Before testing your new script - check any Parameter be sure that password and message is set. 

### Break down into end to end tests

Run the script

```
sudo /bin/bash -c "cd .scripts; ./disk_space_monitor.sh"
```

This should give you all necessary information whats going on.

## Deployment

Follow the instructions in this readme to deploy this script to your live-system 
The Script was tested on Ubuntu18.04 | Raspbian 9.8


## Contributing

Please read [CONTRIBUTING.md]() for details on our code of conduct, and the process for submitting pull requests to us.


## Authors

* **Kevin O. H. Heim** - *Initial work* - [4ddev](https://github.com/4ddev)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

