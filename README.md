# AURORA

已闭源发布，只用开源的可以绕行

[README_EN](https://github.com/aurora-develop/aurora/blob/main/README_EN.md)

（带UI）免费的GPT3.5，支持使用3.5的access 调用


# Web端 

访问http://你的服务器ip:8080/web

![web使用](https://jsd.cdn.zzko.cn/gh/xiaozhou26/tuph@main/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-04-07%20111706.png)


### 注：仅ip属地支持免登录使用ChatGpt可以使用(也可以自定义Baseurl来绕过限制)


### Docker部署
## Docker部署
您需要安装Docker和Docker Compose。

```bash
docker run -d \
  --name aurora \
  -p 8080:8080 \
  ghcr.io/aurora-develop/aurora:latest
```
## 更新容器

```bash
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower -cR aurora --debug
```
## 现闭源发布

## Deploy

### Glitch部署

[![Deploy to Glitch](https://cdn.glitch.com/2703baf2-b643-4da7-ab91-7ee2a2d00b5b%2Fremix-button.svg)](https://github.com/aurora-develop/aurora-glitch)

### Vercel部署

由于vercel的go不支持流式，如果在vercel部署请在STREAM_MODE中填False，不支持任何默认流式的客户端，支持沉浸式翻译。

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Faurora-develop%2Faurora&env=STREAM_MODE&project-name=aurora&repository-name=aurora)

### Render部署
[![Deploy](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)

### Koyeb部署
地区选美国

[![Deploy to Koyeb](https://www.koyeb.com/static/images/deploy/button.svg)](https://app.koyeb.com/deploy?type=docker&name=aurora&ports=8080;http;/&image=ghcr.io/aurora-develop/aurora)

### Railway部署
[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/jcl2Es?referralCode=XXqY_5)

### Zeabur部署
进入修改镜像名称aurora+任何字母数字

[![Deploy on Zeabur](https://zeabur.com/button.svg)](https://zeabur.com/templates/JF3EFW)

## Docker Compose部署
创建一个新的目录，例如aurora-app，并进入该目录：
```bash
mkdir aurora
cd aurora
```
在此目录中下载库中的docker-compose.yml文件：

```bash
docker-compose up -d
```

## Usage

```bash
curl --location 'http://你的服务器ip:8080/v1/chat/completions' \
--header 'Content-Type: application/json' \
--data '{
     "model": "gpt-3.5-turbo",
     "messages": [{"role": "user", "content": "Say this is a test!"}],
     "stream": true
   }'
```

## 高级设置

默认情况不需要设置，除非你有需求

### 环境变量
```

BASE_URL="https://chat.openai.com/backend-api" 代理网关
Authorization=your_authorization  用户认证 key。
TLS_CERT=path_to_your_tls_cert 存储TLS（传输层安全协议）证书的路径。
TLS_KEY=path_to_your_tls_key 存储TLS（传输层安全协议）证书的路径。
PROXY_URL=your_proxy_url 添加代理池来。
```

## 鸣谢

感谢各位大佬的pr支持，感谢。


## 参考项目


https://github.com/xqdoo00o/ChatGPT-to-API

## License

MIT License

========================================================================================================================================================================

首先感谢@xiaofei xiao等贡献者的项目GitHub - aurora-develop/aurora: free 60

如果你的鸡儿跑这个项目会报错 一般都是ip问题 项目是支持Proxy的。这里要请出IP界大善人https://my.socks5.io/ （含AFF） 16 提供免费动态住宅和机房IP。

【全球代理IP免费用】！免费用！免费用！
全球200+国家，9000w+动态IP，没任何费用！
动态住宅IP/静态住宅IP/机房IP等，永久免费！

官网：https://my.socks5.io#JFZVLCYUBR 16 【AFF链接补贴家用】
点击注册，永久免费海外IP.

目前aurora已闭源，将 aurora-linux-amd64.tar.gz 9 解压

cp env.template .env

编辑.env 补充代理信息PROXY_URL=http://user:pass@proxy.socks5.io:3004

运行./aurora 看看日志

如果聊天仍然报错，curl http://refresh.socks5.io/refresh?user=yourusername&country=&state=&city= 切换下IP。这个链接在https://my.socks5.io/ （含AFF） 16 生成代理信息后能看到

没问题的话，crontab加个任务每五分钟刷新IP */5 * * * * curl http://refresh.socks5.io/refresh?user=yourusername&country=&state=&city=

后台运行aurora nohup ./aurora >/dev/null 2>&1 &

也试了docker, docker-compose.yml加环境变量好像没生效(聊天仍然报错)不知道怎么回事，佬们帮忙看看

version: '3'
services:
  app:
    image: ghcr.io/aurora-develop/aurora:latest
    container_name: aurora
    restart: unless-stopped
    ports:
      - '8080:8080'
    environment: 
      - PROXY_URL=http://user:pass@proxy.socks5.io:3004
早上起来发现code: 407 Proxy Authorization Required。免费流量用完了，改成AFF链接补贴家用…
