# go-pusher

English | [简体中文](README_ZH.md)

go-pusher is a tool that can help you upload files to oss and backup file to vps regularly.

## Requirements

- `Go 1.20` and above.

## Features

- [x] upload file to OSS if the file does not exist in OSS or the file in OSS is different from the local file
- [ ] backup local file to VPS regularly

## Usage

- build bin

  `go build main.go`

- add execute permission

  `chmod +x ./main`

- run with config

  `./main -configPath "Your config file abstract path"`

## Config file

Config file is like following:

```toml
modes = ["pusher", "syncer"]

[syncer]
# local directory abstract path
local-path = "xxx"
# remote directory abstract path
remote-path = "xxx"
# time to check file change(second)
interval = 1

[pusher]
# oss provider( now support: qiniu)
oss-provider = "qiniu"
# 待推送目录对应 oss 的前缀
oss-object-prefix = "blog/public"
# 推送到 oss 超时时间（秒）
push-timeout = 60
# 本地待检测文件夹绝对路径
local-directory = "/path/to/push"
# 是否和本地强一致，即本地不存在的文件会从 oss 中删除
oss-delete-not-exists = false

[oss-qiniu]
bucket = "xxx"
# 存储区域
# 华东 z0、华东浙江 2 区 cn-east-2、华北 z1、华南 z2、北美 na0、新加坡 as0、亚太首尔 1 区 fog-cn-east-1（详见 https://developer.qiniu.com/kodo/1238/go）
region = "ZoneHuadong"
access-key = "xxx"
sercet-key = "xxx"
```

## why cretea go-pusher

## [LICENSE](LICENSE)
