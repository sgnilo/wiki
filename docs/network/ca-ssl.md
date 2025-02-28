---
categories: [网络]
tags: [SSL, CA, certbot, nginx]
---

# 通过 Let's Encrypt 申请根CA提供验证的 SSL 证书

- 常用的云服务商（腾讯云、阿里云提供的）免费证书有效期短（90天），申请麻烦，还有限额，限额用完就没招了
- 一年期的证书花钱买很贵，支持通配符域名的一年约2K左右。
- 自签名证书浏览器、手机不认，除非手动安装自签名CA证书，这几乎相当于无法在生产环境中使用

well，那么[Let's Encrypt](https://letsencrypt.org/getting-started/) 是个不错的选择，可提供：
- 90天的通配符域名免费验证发放
- 脚本化的申请体验（即可提供自动化申请部署，方便省心）

## Lets Encrypt 通过 [ACME](https://zh.wikipedia.org/wiki/%E8%87%AA%E5%8B%95%E6%86%91%E8%AD%89%E6%9B%B4%E6%96%B0%E7%92%B0%E5%A2%83) 协议申请部署

### Step1 选择一个合适的 ACME client

这里由于我们的环境里有anaconda，那就直接用 python 版本的 certBot。附上其他的 [client 列表](https://letsencrypt.org/docs/client-options/)。

### 安装 [certBot](https://certbot.eff.org/instructions?ws=nginx&os=pip)

首先安装依赖，要求 python3 环境

```sh
yum install augeas-libs # dnf install augeas-libs 也可
```

然后删掉系统中可能存在的旧的 certBot
```sh
sudo yum remove certbot
```
创建一个python虚拟执行环境

```sh
python -m venv /opt/certbot/
```

安装certBot
```sh
pip install certbot certbot-nginx
```

创建软连接，将python环境中的 certbot 软链到 系统命令中，这样就可以直接使用certbot命令了
```sh
ln -s /home/work/anaconda/bin/certbot /usr/bin/certbot
```
### 生成证书
尝试使用certbot生成证书
```sh
certbot certonly --nginx # 仅生成证书
```

或者，直接使用certbot去生成证书并部署（自动修改nginx配置）
```sh
certbot --nginx # 生成证书并部署
nginx -s reload # 重启nginx
```

检查浏览器访问，此时应该可以发现 https 已经生效

### 自动到期更新

当3个月有效期过了的时候，需要重新申请证书。certbot提供了自动去到期申请新的证书的功能

```sh
echo "0 0,12 * * * root python -c 'import random; import time; time.sleep(random.random() * 3600)' && sudo certbot renew -q" | tee -a /etc/crontab > /dev/null
```



  
