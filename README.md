# docker-mc-valhelsia-3
Docker setup for Minecraft

# How to
1. Run preup.sh for preinstalling mod into volume
2. Run up.sh for running the minecraft server
3. For backup use backup.sh (automization via cron_backup.sh possible)
4. Run down.sh for stopping the containers and cleanup

# Automatic restart from one docker container to another

For setting up cron its mostly based upon this stackoverflow entry: https://stackoverflow.com/questions/37458287/how-to-run-a-cron-job-inside-a-docker-container

1. Run a privileged container with crontab and docker inside of it: `docker run -it --rm --privileged --name cron-docker -v /var/run/docker.sock:/var/run/docker.sock docker:latest /bin/sh`
2. Create a new file in /etc/cron.d for the job named "cron-docker": `touch /etc/cron.d/cron-docker`
3. Inside this file enter your cron-schedule, like this: 10 6 * * * docker restart mc_valhelsia_3_minecraft_1
4. Give it execution right: `chmod 0644 /etc/cron.d/cron-docker`
5. Apply cron job: `crontab /etc/cron.d/cron-docker`
6. Run cron: `cron`
