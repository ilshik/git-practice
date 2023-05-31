# git-practice
git 실습

To set up Git in a closed network, you can follow the steps below:

1. Create a new user. Git uses SSH for authentication and all traffic between servers and clients, so you’ll need a service user to manage the repo.
```bash
sudo useradd git
```

2. Switch to the git user for the rest of the setup:
```bash
su git
```

3. Add your SSH keys to the git user’s authorized_keys file.

4. Create a new directory for your Git repositories:
```bash
mkdir /srv/git
```

5. Change the owner of this directory to the git user:
```bash
chown git:git /srv/git
```

6. Create a new repository:
```bash
cd /srv/git
mkdir my_project.git
cd my_project.git
git init --bare --shared
```

7. On the developer machines, clone the repository:
```bash
git clone <USERNAME>@<IP_ADDRESS>:/srv/git/my_project.git
```

You can find more detailed information on how to set up Git in a closed network in this [HowToGeek article](https://www.howtogeek.com/devops/how-to-set-up-a-private-git-server/) and this [StackOverflow thread](https://stackoverflow.com/questions/32715762/how-to-setup-a-git-repository-on-local-network).

출처: Bing과의 대화, 2023. 5. 31.
(1) How to setup a git repository on local network? - Stack Overflow. https://stackoverflow.com/questions/32715762/how-to-setup-a-git-repository-on-local-network.
(2) Using Git across multiple systems without network access. https://superuser.com/questions/1367571/using-git-across-multiple-systems-without-network-access.
(3) How to Set Up a Private Git Server. https://www.howtogeek.com/devops/how-to-set-up-a-private-git-server/.