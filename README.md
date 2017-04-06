# ansible-in-docker
Dockerfile for ansible in docker

```bash
git clone git@github.com:amasucci/ansible-in-docker.git
docker build --squash -t ansible:b0 .
docker run --rm ansible:b0
```
