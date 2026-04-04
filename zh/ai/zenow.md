---
sidebar_position: 14
---

# 知了（zenow）

**知了（zenow）** 是一款运行于本地的 AI 知识助手桌面应用，基于 Electron + React + FastAPI 构建，通过 llama-server 在本地运行 GGUF 格式的大语言模型，支持多模型并行管理、知识库问答等功能，保护用户数据隐私。

## 平台支持情况

| 平台&系统     | 是否支持加速 |
|----------|------------|
| K1 Bianbu LXQT/GNOME       | 不支持        |
| K1 Buildroot   | 不支持 |
| K1 OpenHarmony5.0 | 不支持 |
| K3 Bianbu LXQT/GNOME      | 支持        |
| K3 Buildroot   | 不支持 |

## 技术栈

应用了哪些技术点
例：
LLM SDK (链接)
SPEECH SDK （链接）
...

## 框架图

一张漂亮的展示应用框架结构的图

## 安装

```bash
sudo apt update
sudo apt install zenow llm-sdk sm-sdk
```

## 使用

### 启动

点击左下角 Windows 菜单，搜索 **zenow** 或 **知了** 即可找到并启动应用。

> 💡 可右键应用图标，选择"添加到桌面"，方便下次快速启动。

![](../static/zenow_add.png)


### 下载模型

进入**设置页面**，点击模型列表，选择所需模型即可开始下载。

![](../static/zenow_install_model.png)

支持同时点击多个模型并发下载。

![](../static/zenow_select_model.png)


### 启用模型

下载完成后，再次点击已下载的模型，等待状态灯由红色变为绿色（提示"模型启动成功"），即可开始使用。

![](../static/zenow_all_ready.png)


> 为保障知识库功能的完整性，建议至少各下载并启动一个 **LLM**、**Embed**、**Rerank** 模型。

启动成功后即可使用**新对话**和**知识库**等功能。

### 直接聊天

### 知识库导入

### 基于知识库聊天

### 语音输入输出

### 设置参数说明

## 性能



