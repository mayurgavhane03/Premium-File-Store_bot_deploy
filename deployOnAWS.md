**Setting up Supervisor to Manage Your Script**
=====================================================

Supervisor is a great way to manage the running of your script. It's a client/server system that allows its users to monitor and control a number of processes on UNIX-like operating systems.

**Step 1: Install Supervisor**
-----------------------------

sudo apt-get update
sudo apt-get install supervisor

**Step 2: Create a Supervisor Configuration File**
---------------------------------------------

sudo nano /etc/supervisor/conf.d/mybot.conf

[program:mybot]
command=/home/ubuntu/Premium-File-Store_bot_deploy/venv/bin/python3 /home/ubuntu/Premium-File-Store_bot_deploy/main.py
directory=/home/ubuntu/Premium-File-Store_bot_deploy
autostart=true
autorestart=true
stderr_logfile=/var/log/mybot/mybot.err.log
stdout_logfile=/var/log/mybot/mybot.out.log
user=ubuntu

**Step 3: Create Log Directory**
------------------------------

sudo mkdir -p /var/log/mybot
sudo chown ubuntu:ubuntu /var/log/mybot

**Step 4: Update Supervisor and Start Your Script**
------------------------------------------------

sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl start mybot

**Step 5: Verify that the Script is Running**
-----------------------------------------

sudo supervisorctl status mybot

This setup will ensure that main.py runs continuously and restarts automatically if it crashes. It also keeps logs of the script's output and errors, which can be useful for debugging.