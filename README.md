# 基于以下开源项目

- [ZY-Player-Web](https://github.com/Hunlongyu/ZY-Player-Web) | [Forked](https://github.com/HV-LIVE/zy-player-web)

# 同步构建结果

- 编译 [zy-player-web](https://github.com/HV-LIVE/zy-player-web) 项目，从源项目同步以下文件到本项目中：

  - 将源项目 `docs` 目录下的所有内容同步到本项目 `zy-player-web` 目录中

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

# 配置列表

| 环境变量          | 默认值 | 说明                                                 |
| ----------------- | ------ | ---------------------------------------------------- |
| HV_HTTP_PORT      | 80     | 容器内的 HTTP 端口（如果指定了证书就是 HTTPS 端口）  |
| HV_HTTPS_CERT     |        | 容器内的证书 pem 文件路径（指定后会开启 HTTPS 协议） |
| HV_HTTPS_CERT_KEY |        | 容器内的证书 key 文件路径（指定后会开启 HTTPS 协议） |
