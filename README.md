# resty-upload-rate-limit

### this repo keeps a minimum openresty configuration and some lua code, show you how to limit upload rate.

#### [关于这个功能的思路和一些想法](https://yukityan.cc/openresty-xian-zhi-wen-jian-shang-chuan-su-du/)

#### setup
```console
foo@bar> git clone https://github.com/luvjoey1996/resty-upload-rate-limit.git
foo@bar> cd resty-upload-rate-limit
foo@bar> mkdir logs
foo@bar> openresty -p `pwd` -c nginx.conf
```

#### test
```console
foo@bar> curl 127.0.0.1:8888 -T {some file}
```

#### main code
```lua
-- iter req body, limit upload speed in 200kb/s
for chunk in limit_recv_body(200) do
    ngx.req.append_body(chunk)
end
```

#### demo
![截图_2020-08-03_23-37-17.png](https://i.loli.net/2020/08/03/Z5JlBWvPNEpYhsk.png)
