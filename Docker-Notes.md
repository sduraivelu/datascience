#### Running docker-compose
* $ `sudo docker-compose up`
* Error: `Unsupported config option for services service: 'web'`
  * [StackOverflow says](http://stackoverflow.com/questions/36724948/docker-compose-unsupported-config-option-for-services-service-web) I need to be using 1.6 (or later) version of docker-compose.  I was running version 1.3 that I got from `apt-get`.
  * For a list of versions, see the [Compose file format compatibility matrix](https://github.com/docker/compose/releases)
* Error: `Couldn't connect to Docker daemon at http+docker://localunixsocker - is it running?`
  * Had to add `sudo` per [here](https://forums.docker.com/t/cannot-connect-to-the-docker-daemon-is-the-docker-daemon-running-on-this-host/8925/4)

#### Per crimzie:
* You can see the docker compose setup in docker-compose.yml in root folder.  When used, it pulls two latest docker images from a repository (hamstoo backend and mongo db), runs them in a docker virtual machine and sets up their environment automatically.

#### Installation
* Don't use `sudo apt-get install docker docker-compose docker-engine` to install Docker.  Instead follow the steps below.
  1. Remove all existing Docker packages using the following commands: `apt list --installed | grep docker` and `sudo apt-get remove <docker_package>`
  2. Follow the 'Install using the repository' instructions [here](https://docs.docker.com/engine/installation/linux/ubuntu/).
    * "Before you install Docker for the first time on a new host machine, you need to set up the Docker repository."
  4. Continue on the same page through the 'Install Docker' section instructions, which will install `docker-engine` (version 1.12.6 at time of writing, 2/1/17)
  5. Per step #3-4 on [this](https://docs.docker.com/compose/install/) page, go to [here]() and run the following commands:
    * `$ sudo -i`
    * ``# curl -L https://github.com/docker/compose/releases/download/1.10.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose``
    * `chmod +x /usr/local/bin/docker-compose`
  6. But then I was getting an error when running docker-compose from the PATH (when running with the full absolute path, `/usr/local/bin/docker-compose`--note the additional 'local'--it worked fine)
    * Here's the error: `bash: /usr/bin/docker-compose: No such file or directory`
    * Here was the fix: `sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`
    * [Here](http://superuser.com/questions/787897/docker-hello-world-example-doesnt-work-no-such-file-or-directory/789480) was someone with a similar issue, which I commented on.