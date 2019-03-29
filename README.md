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
sudo chmod 600 .scripts
```

Download and create the Source file 

```
sudo curl https://raw.githubusercontent.com/4ddev/Disk-Space-Monitor/master/disk_space_monitor > disk_space_monitor.sh
```

Change file permissions 

```
sudo chmod 700 .scripts/disk_space_monitor.sh
```

Create a file which stores the smtp password - 

```
sudo echo "YOUR PASSWORD HERE" > .scripts/smtp_pw.txt
```

Create a file which contains the mail body 

```
sudo echo "Some default message which is send in any mail"  > .scripts/message.txt
```


Open the file by  typing 

```
sudo nano .scripts/disk_space_monitor.sh 
```

Change these parameters to your needs 

```
# PROJECT NAME this will be added to the Subject 
PROJECT_NAME="PROJECT_NAME"

# Location of your password File - dont forget to change the file permissions!
AUTH_PASSWORD="/opt/bin/.scripts/smtp_pw.txt"

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

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
