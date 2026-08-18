# sublinkpro 部署配置

基于 [zerodeng/sublink-pro](https://github.com/zerodeng/sublink-pro) 镜像的订阅聚合工具部署配置 + 自定义模板。

部署位置：HostDare `103.79.118.103:8000`（公网 `https://sublink.0909106.xyz`）与本地 `192.168.1.45:8000` 双跑。

## 内容

- `docker-compose.yml`：服务编排（端口 8000、DB/template/logs 挂载、`SUBLINK_*` 环境变量）
- `template/clash.yaml`、`template/surge.conf`：自定义订阅输出模板

## 部署

```bash
cp docker-compose.yml 到部署目录后：
docker compose up -d
```

环境变量说明（见 compose）：

| 变量 | 说明 |
|---|---|
| `SUBLINK_PORT` | 服务端口 |
| `SUBLINK_LOG_LEVEL` | 日志级别 |
| `SUBLINK_CAPTCHA_MODE` | 验证码模式 |
| `SUBLINK_EXPIRE_DAYS` | 订阅过期天数 |
| `SUBLINK_ADMIN_PASSWORD` | 管理密码（部署时改为强密码） |

## 注意

- `db/`（订阅数据 64M）与 `logs/` 为运行时数据，**不入库**
- 本地 45 的部署作为内网聚合源（走 Cloudflare Tunnel 暴露）