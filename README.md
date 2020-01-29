# Docker Swarm Flask Redis

## Usage

Init swarm
```bash
sudo docker swarm init
```

Start a registry as a service on your swarm
```bash
sudo docker service create --name registry --publish published=5000,target=5000 registry:2

# returns `{}` on successful registry setup
curl http://localhost:5000/v2/
```

Deploy stack to swarm
```bash
sudo docker stack deploy -c docker-compose.yml demo
```

Check services of stack
```bash
sudo docker stack services demo
```

Should increment counter on successive hits
```bash
curl http://localhost:8000
```

Teardown
```bash
sudo docker stack rm demo

sudo docker service rm registry
```

Bring your Docker Engine out of swarm mode
```bash
sudo docker swarm leave --force
```

## Resources

- Docker Doc [Deploy a stack to a swarm](https://docs.docker.com/engine/swarm/stack-deploy/)
- Learn more on [Docker Service](https://docs.docker.com/engine/reference/commandline/service/)