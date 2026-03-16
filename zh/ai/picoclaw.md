<!--
 * Copyright 2022-2023 SPACEMIT. All rights reserved.
 * Use of this source code is governed by a BSD-style license
 * that can be found in the LICENSE file.
 * 
 * @Author: David(qiang.fu@spacemit.com)
 * @Date: 2026-03-16 17:10:31
 * @LastEditTime: 2026-03-16 17:18:05
 * @FilePath: \doc\docs-bianbu\zh\ai\picoclaw.md
 * @Description: 
-->
---
sidebar_position: 7
---

# picoClaw

## 1. 下载Go

```bash
sudo apt update
sudo apt install golang
```

## 2. 下载源码并编译

```bash
git clone https://github.com/sipeed/picoclaw.git
cd picoclaw
make deps
make build
make install
```

## 3. 配置环境变量及模型
由于/home/bianbu/.local/bin/picoclaw不在系统环境变量中

```bash
sudo cp /home/bianbu/.local/bin/picoclaw /usr/local/bin/
```

## 4. 运行pipoclaw onboard

```bash
pipoclaw onboard
```

## 5. 配置模型

```bash
vim /home/bianbu/.picoclaw/config.json
```

## 6. 验证

```bash
picoclaw agent -m "What is 2+2?"
```
