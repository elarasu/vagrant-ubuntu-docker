# Readme
Instructions to seed the dev environment.  Very specific environment via vagrant to setup

   * ubuntu
   * ansible
   * git tools
   * languages {python, nodejs}
   * docker
   * editors {vi,emacs}

# Pre-requisite
On Mac, Vagrant v1.6.3 or above

   * git client
   * python, easy_install, pip `sudo easy_install pip`
   * ansible pkgs `sudo pip install paramiko PyYAML jinja2 httplib2`

# Instructions
First clone this repository to your box and have pre-requsites installed.

```
   $ cd vagrant-ubuntu-docker
   $ git clone git://github.com/ansible/ansible.git --recursive
   $ source ansible/hacking/env-setup
   $ vagrant up
   $ vagrant ssh
```

# update to git changes
Ongoing updates to changes in git repo

```
   $ cd vagrant-ubuntu-docker
   $ git pull 
   $ source ansible/hacking/env-setup
   $ vagrant provision / vagrant reload (port changes)
```

