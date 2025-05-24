# Docker Labs Based on "Using Docker" by Adrian Mouat

This repository contains a series of practical labs based on the book _Using Docker_ by Adrian Mouat. Each lab focuses on specific Docker features and follows the typographical conventions from the book — only commands shown in **Constant width bold** are included.

> ⚠️ These labs assume you have Docker installed and configured on your machine.

---

## Lab 1: First Steps with Docker (Chapter 3)

**Objective:** Get comfortable running and managing containers.

### Tasks:

```bash
docker run -h CONTAINER -i -t debian /bin/bash
mv /bin /basket
ls
docker ps
docker run -it --name cowsay --hostname cowsay debian bash
apt-get update
apt-get install -y cowsay fortune
/usr/games/fortune | /usr/games/cowsay
ls Dockerfile
docker build -t test/cowsay-dockerfile .
docker stop myredis
docker rm -v myredis
docker rm $(docker ps -aq)
```

---

## Lab 2: Docker in Development (Chapter 5)

**Objective:** Use Docker for local development.

### Tasks:

```bash
tree identidock/
docker run -d -P --name port-test identidock
docker port port-test
```

---

## Lab 3: Creating a Simple Web App (Chapter 6)

**Objective:** Clone and prepare a web app project.

### Tasks:

```bash
git clone -b v0 https://github.com/using-docker/creating-a-simple-web-app/
```

---

## Lab 4: Image Distribution (Chapter 7)

**Objective:** Distribute Docker images and manage Git history.

### Tasks:

```bash
git clone -b v0 https://github.com/using-docker/image-dist/
git add README.md
git commit -m "Added README"
git push
```

---

## Lab 5: Continuous Integration with Docker (Chapter 8)

**Objective:** Use Docker in CI workflows.

### Tasks:

```bash
git clone -b v0 https://github.com/using-docker/ci-testing/
```

---

## Lab 6: Container Deployment (Chapter 9)

**Objective:** Deploy containers using shell scripts and Ansible.

### Tasks:

```bash
git clone -b v0 https://github.com/using-docker/deploying-containers/
curl localhost:5000/monster/gordon | head -c 4
docker-machine scp deploy.sh identihost-do:~/deploy.sh
docker-machine ssh identihost-do
chmod +x deploy.sh
./deploy.sh
docker run -it \
  -v ${HOME}/.ssh:/root/.ssh:ro \
  -v $(pwd)/identidock.yml:/ansible/identidock.yml \
  -v $(pwd)/hosts:/etc/ansible/hosts \
  --rm=true generik/ansible ansible-playbook identidock.yml
```

---

## Lab 7: Logging and Monitoring (Chapter 10)

**Objective:** Monitor container performance.

### Tasks:

```bash
git clone -b v0 https://github.com/using-docker/logging/
docker stats $(docker inspect -f {{.Name}} $(docker ps -q))
```

---

## Lab 8: Networking and Service Discovery (Chapter 11)

**Objective:** Use Docker networking and the Ambassador pattern.

### Tasks:

```bash
eval $(docker-machine env identidock-host)
docker run -d --name redis_ambassador --expose 6379 \
  -e REDIS_PORT_6379_TCP=tcp://$(docker-machine ip redis-host):6379 \
  amouat/ambassador
```

---

## Lab 9: Orchestration and Management (Chapter 12)

**Objective:** Work with Swarm and Kubernetes.

### Tasks:

```bash
git clone -b https://github.com/using-docker/orchestration/
eval $(docker-machine env --swarm swarm-master)
docker info
kubectl create -f redis-controller.json services/redis
kubectl get services identidock
curl 23.251.128.247
```

---

## Lab 10: Security and Limiting Containers (Chapter 13)

**Objective:** Apply security best practices and resource limits.

### Tasks:

```bash
docker run --user 1000 ubuntu:trusty ps aux
docker run --rm ubuntu:trusty sudo ps aux
docker run --cap-drop all debian chown 100 /tmp
docker run --cap-drop all --cap-add CHOWN debian chown 100 /tmp
time docker run --ulimit cpu=12:14 amouat/stress stress --cpu 1
time docker run --ulimit nofile=64000:64000 debian ls -l /proc/self/fd
sestatus
restorecon -Rv /var/lib/docker
```

---

## License

Content adapted for educational use from *Using Docker* by Adrian Mouat. All trademarks and copyrights are property of their respective owners.
