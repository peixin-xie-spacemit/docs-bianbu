<!--
 * Copyright 2022-2023 SPACEMIT. All rights reserved.
 * Use of this source code is governed by a BSD-style license
 * that can be found in the LICENSE file.
 * 
 * @Author: David(qiang.fu@spacemit.com)
 * @Date: 2026-02-28 14:50:46
 * @LastEditTime: 2026-02-28 16:53:10
 * @FilePath: \doc\docs-bianbu\zh\ai\llama-cpp.md
 * @Description: 
-->
<!--
 * Copyright 2022-2023 SPACEMIT. All rights reserved.
 * Use of this source code is governed by a BSD-style license
 * that can be found in the LICENSE file.
 * 
 * @Author: David(qiang.fu@spacemit.com)
 * @Date: 2026-02-28 11:14:51
 * @LastEditTime: 2026-02-28 14:50:46
 * @FilePath: \doc\docs-bianbu\zh\ai\llama-cpp.md
 * @Description: 
-->
---
sidebar_position: 2
---

# llama.cpp

![](../static/llama-cpp-icon.png)

**llama.cpp** 是一个用纯 C/C++ 写的开源推理框架，专门让 Llama 等 GGUF/GGML 格式的大语言模型能在本地 CPU/GPU（笔记本、手机、树莓派甚至浏览器）快速运行，而无需依赖重量级框架。

## 平台支持情况

| 平台&系统     | 是否支持加速 |
|----------|------------|
| K1 Bianbu LXQT/GNOME       | 支持        |
| K1 Buildroot   | 不支持 |
| K1 OpenHarmony5.0 | 不支持 |
| K3 Bianbu LXQT/GNOME      | 支持        |
| K3 Buildroot   | 不支持 |

## Bianbu LXQT/GNOME环境使用说明

### 安装

打开终端，执行如下命令安装llama.cpp

```bash
sudo apt update
sudo apt install llama.cpp-tools-spacemit
```

### 下载模型

spacemit-llama.cpp 目前支持三种量化格式的加速模型：
- Q4_K_M
- Q4_0 
- Q4_1

根据芯片平台的算力下载合适参数的模型，K1平台推荐Qwen3-0.6B，下载方法如下：

```bash
wget https://www.modelscope.cn/models/unsloth/Qwen3-0.6B-GGUF/resolve/master/Qwen3-0.6B-Q4_0.gguf -P ~/
```

K3平台推荐Qwen3-30B-A3B，下载方法如下：

```bash
wget https://www.modelscope.cn/models/unsloth/Qwen3-30B-A3B-Instruct-2507-GGUF/resolve/master/Qwen3-30B-A3B-Instruct-2507-Q4_0.gguf -P ~/
```

### 使用

有3种常见的使用方法
- llama-bench
- llama-cli
- llama-server

下面以K3平台为例，分别介绍

#### llama-bench


```bash
llama-bench -m Qwen3-30B-A3B-Instruct-2507-Q4_0.gguf -t 8 -p 64 -n 64 -mmp 0 -fa 1
```

输出结果如下：

![](../static/llama-bench.png)

#### llama-cli

```bash
llama-cli -m Qwen3-30B-A3B-Instruct-2507-Q4_0.gguf -t 8 --no-mmap -c 15360
```

输出结果如下：
![](../static/llama-cli.png)

#### llama-server

启动后台llama-server服务：

```bash
llama-server -m Qwen3-30B-A3B-Instruct-2507-Q4_0.gguf -t 8 --host 127.0.0.1 --port 8080 --ctx-size 15360 --n-gpu-layers 0 --batch-size 512 --metrics --no-mmap &
```

##### 本地API请求

```bash
curl -X POST http://127.0.0.1:9090/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
        "model": "Qwen3-0.6B",
        "messages": [
          { "role": "user", "content": "介绍珠海？" }
        ]
      }'
```

输出结果如下：
![](../static/llama-server-api.png)


##### 浏览器请求

在浏览器中搜索 `http://localhost:8080` 打开 llama 服务器，直接在浏览器中使用 llama.cpp

![](../static/llama-server-chrome.png)

