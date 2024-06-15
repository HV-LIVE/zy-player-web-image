# 基于以下开源项目

- [ZY-Player-Web](https://github.com/Hunlongyu/ZY-Player-Web) | [Forked](https://github.com/HV-LIVE/zy-player-web)

# 同步构建结果

- 先编译 [zy-player-web](https://github.com/HV-LIVE/zy-player-web) 项目，然后将 `docs` 目录下的文件同步到本项目 `zy-player-web` 目录下

- 当前同步的分支: [main](https://github.com/HV-LIVE/zy-player-web/tree/main) 

- 当前同步的提交: [b9fed3b](https://github.com/HV-LIVE/zy-player-web/commit/b9fed3b97ad95429435bab16b5ec6d7552ef84d7)

# 编译镜像

```sh
docker build -t hvlive/zy-player-web:latest .
```

# 部署镜像

```sh
# HTTP
docker run -d --restart=unless-stopped \
    --name zy-player-web \
    -p {host_port}:80 \
    hvlive/zy-player-web:latest

# HTTPS
docker run -d --restart=unless-stopped \
    --name zy-player-web \
    -p {host_port}:80 \
    -v {host_cert_path}:{container_cert_path} \
    -e HV_HTTPS_CERT={container_cert_path}/{pem_file} \
    -e HV_HTTPS_CERT_KEY={container_cert_path}/{key_file} \
    hvlive/zy-player-web:latest
```
