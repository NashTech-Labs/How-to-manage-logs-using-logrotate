# Short Description about this template
This template help to manage the logs file using logrotate

* While keeping the logs in a single files it will store the logs and make a big amount file and it is difficult for troubleshooting. For solve this problem we can use logrotate.Logrotate manage the logs on hourly , daily, monthly and yearly basis. 

In this template i am using a python script and run script as background service which produce some log that i am  store  in the Output.log and Error.log files.Using the logrotate.conf file we can manage the logs and perform some operation  according to the need.In the logrotate.conf file  `/home/knoldus/logs/Output.log` is the path where my log are store (you can set your directory path where the logs file Present)


Note - Here i am using python script you can use any script like java ,c etc. 


# Steps for Execution 

1. `sudo vi /etc/systemd/system/pulse.service`     

here `pulse.service` is the service file.
 

2. `sudo systemctl daemon-reload`

3. `sudo systemctl enable pulse.service`

   This command will create a symlink

4. `sudo systemctl start pulse.service`

This command is used for start the service.

5. `sudo systemctl status pulse.service`
This command is used for check the service is running or not


6. Here i going to run as a cronjob for that run the command from terminal `crontab -e`

7. For running the cronjob on every hour we pass this command

`1 * * * * /usr/sbin/logrotate /home/knoldus/test.conf –state /home/knoldus/logrotate-state.`
 
For more details visit this link  - https://blog.knoldus.com/what-is-logrotate-and-its-uses/
