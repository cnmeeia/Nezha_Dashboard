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