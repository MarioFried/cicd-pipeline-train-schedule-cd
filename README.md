# cicd-pipeline-train-schedule-cd

This is a simple train schedule app written using nodejs. It is intended to be used as a sample application for a series of hands-on learning activities.

## Running the app

You need a Java JDK 7 or later to run the build. You can run the build like this:

    ./gradlew build

You can run the app with:

    ./gradlew npm_start

Once it is running, you can access it in a browser at [http://localhost:3000](http://localhost:3000)

------------
---------------
A few notes about the lab server setup:

A systemd service called train-schedule has already been created on both web servers. 
The train-schedule app can be controlled with systemd using commands like systemctl stop train-schedule and systemctl start train-schedule.
The train-schedule service expects the application code to be deployed to /opt/train-schedule.
A deployment user has already been created on both web servers. It can write to /opt/train-schedule as well as start and stop the train-schedule service. 
The username is deploy and the password is jenkins. Jenkins can use these credentials in order to perform the deployment.
The Publish Over SSH plugin is already installed on the Jenkins server.
The Jenkins server listens on port 8080. Train Schedule, once it is deployed, will listen on port 3000.

---------------------
systemctl (/etc/systemd/system/train-schedule.service)

[Unit]
Description=Train Schedule
After=network.target

[Service]

Type=simple
WorkingDirectory=/opt/train-schedule
ExecStart=/usr/bin/node bin/www
StandardOutput=syslog
StandardError=syslog
Restart=on-failure

[Install]
WantedBy=multi-user.target
------------------------------------------
Instalar o NODE.JS

$ curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -
$ sudo yum install nodejs
$ node --versin
$ npm --version

