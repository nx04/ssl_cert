安装 Certbot
先安装 EPEL 仓库（因为 certbot 在这个源里，目前还没在默认的源里）

```
sudo yum install epel-release
```

安装 certbot
```
sudo yum install certbot

```

查看 certbot 版本，因为 ACME v2 要在 certbot 0.20.0 以后的版本支持。

```
certbot --version
```

certbot 1.11.0

申请证书
申请通配符证书命令如下

```
sudo certbot certonly -d test.yourdomain.com --manual --preferred-challenges dns --server https://acme-v02.api.letsencrypt.org/directory
```
主要参数说明：

- certonly 是 certbot 众多插件之一，您可以选择其他插件。
- -d 为那些主机申请证书，如果是通配符，输入 *.yourdomain.com。
- 注意：本文还申请了 yourdomain.com 这是为了避免通配符证书不匹配。
- –preferred-challenges dns，使用 DNS 方式校验域名所有权。
- 注意：通配符证书只能使用 dns-01 这种方式申请。

