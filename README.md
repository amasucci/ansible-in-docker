# ansible-in-docker
Dockerfile for ansible in docker

```bash
git clone git@github.com:amasucci/ansible-in-docker.git
docker build --squash -t ansible:b0 .
docker run --rm ansible:b0
```

Let's assume you have a playbook `main.yml` with an inventory file called `staging` you can run it by executing this command:
`docker run --rm -it -v ~/.ssh/id_rsa:/root/.ssh/id_rsa -v ~/.ssh/id_rsa.pub:/root/.ssh/id_rsa.pub -v $(pwd):/ansible/playbooks ansible:b0 main.yml -i staging --ask-sudo-pass`

note: we are mounting three volumes, une for the private key, one for the public one and one for the current directory, were the playbook is expected to be found.

this can also be replaced by an alias like this:
```bash 
alias ansible-playbook='docker run --rm -it -v ~/.ssh/id_rsa:/root/.ssh/id_rsa -v ~/.ssh/id_rsa.pub:/root/.ssh/id_rsa.pub -v $(pwd):/ansible/playbooks ansible:b0'```
