# Project Plant Sensing System - Raspberry Pi Gateway - local storage
in this we have th python files that can be used as an example on how to send data to the database on the pi.
in order for this code to work the user needs to install dependencies on the raspberry pi and create the database and table within the database.

before installing anything it is recommended to run the commands:   sudo apt update
                                                                    sudo apt upgrade
after these 2 commands, possibly taking very long are done, run:
```
sudo apt install mariadb-server
sudo mysql_secure_installation
```

follow the prompts and make sure to change the password. The password used in this example is 'plantenna'

after installing the database the user has to log in using the command 
```bash
sudo mysql -u root -p
```
this will ask the user for the password, in this case being 'plantenna'
note that the text will not show up when typing, as with most linux passwords.

now to create the database, we run the commands(note that in mysql you need to send the ';' for the command to execute):
````
create database plantenna;

use plantenna;

create table sensor_data (
number int not null auto_increment primary key,
temperature int(3),
humidity int(3),
battery_voltage int(3),
airflow int(3),
pressure int(3)
);
````

now the database is created with the necessary columns. 
to exit simply run the command ```exit``` or ```quit```

To access the database with python code we need to install the mysql connector.
This is done by executing the following commands:
```
sudo pip3 install mysql-connector-python
```
in the next step we need to remove the create a new user called plantenna@localhost with the password plantenna.
The reason for this is that to run the database using root@localhost we always have to run using sudo, but not using a new user.
This user needs to have all privileges to the database.
To do this run the following:
````
sudo mysql

CREATE USER 'plantenna'@'localhost' IDENTIFIED BY 'plantenna';

GRANT ALL PRIVILEGES ON *.* TO 'plantenna'@'localhost' WITH GRANT OPTION;
````






## Current status
- TBD

## To-do list
- Update README
- Add local storage
