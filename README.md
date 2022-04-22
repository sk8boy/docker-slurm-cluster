docker-slurm-cluster
====================

This is a demonstration of how the Slurm could be deployed in the docker infrastructure using docker compose.

It consist of the following services:
- MariaDB (for accounting data)
- head node (munge, slurmd, slurmctld, slurmdbd)
- compute node x4 (munge, slurmd)

The slurm version is `v20.02.7`

# How to deploy

Clone the repository

```
git clone git@github.com:xtreme-d/docker-slurm-cluster.git docker-slurm-cluster
cd docker-slurm-cluster
```

Next, build the node image.
```
docker-compose build
```

Start the cluster

```
docker-compose up -d
```

To access the head node:

```
docker exec -it axc-headnode bash
```

NOTE: the first running of Slurm might take up to 1 minute because a new MariaDB database initiation procedure is slow a bit.

镜像自动安装openssh-server包，并完成配置。外部使用1022端口，root账号，123456密码可以连接axc-headnode。
```
ssh root@localhost -p 1022
```

