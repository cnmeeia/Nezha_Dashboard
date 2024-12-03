# 

安装 nezha_agent步骤


```powershell
curl -L https://raw.githubusercontent.com/nezhahq/scripts/main/agent/install.sh -o nezha.sh && chmod +x nezha.sh && env NZ_SERVER=IP地址:8008 NZ_TLS=false NZ_CLIENT_SECRET=你的agentsecretkey ./nezha.sh

```

获取 agentsecretkey 

```powershell
docker exec -it nezha-dashboard sh

cd data && cat *.yaml

```

caddy 反代 nezha

```powershell

wget https://github.com/cnmeeia/caddy/releases/download/v0.4.2/caddy

mv caddy /usr/bin && chmod +x /usr/bin/caddy


(ssl_cert) {
    tls /opt/caddy/rsa.pem /opt/caddy/key.pem
}

na.19510272.xyz {
    import ssl_cert
    reverse_proxy http://127.0.0.1:8008
}

```


```powershell
# 使用以下命令验证文件是否语法正确

caddy validate --config /opt/caddy/r2.caddyfile

# 如果验证通过，运行以下命令启动：

caddy run --config /opt/caddy/r2.caddyfile


```