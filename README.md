# docker-mc-valhelsia-3
Docker setup for Minecraft

# How to
1. Run preup.sh for preinstalling mod into volume
2. Run up.sh for running the minecraft server
3. For backup use backup.sh (automization via cron_backup.sh possible)
4. Run down.sh for stopping the containers and cleanup

Automatic restart from one docker container to another
1. Run a privileged container with crontab and docker inside of it: `docker run -it --rm --privileged --name cron-docker -v /var/run/docker.sock:/var/run/docker.sock docker:latest /bin/sh`
2. TODO
