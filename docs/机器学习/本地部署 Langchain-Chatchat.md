---
title: 本地部署 Langchain-Chatchat
date: 2024-01-04
update: 2024-01-04
tags: LLM
---

# 本地部署 Langchain-Chatchat

## 一 环境配置

---

```sh
brew install git-lfs && git lfs install
# 创建虚拟环境
conda create --name LangChat python=3.10
conda activate LangChat
# clone project
cd LLM && git clone https://github.com/chatchat-space/Langchain-Chatchat.git && cd Langchain-Chatchat
# 安装项目的依赖
pip install torch
pip install -r requirements.txt
# pip install -r requirements_api.txt
pip install -r requirements_webui.txt

pip freeze | grep langchain
pip install --upgrade langchain

# 模型下载
git clone https://huggingface.co/THUDM/chatglm3-6b
git clone https://huggingface.co/BAAI/bge-large-zh
```

初始化知识库和配置文件

```sh
# copy 默认配置
python copy_config_example.py
# 初始化或者重建向量数据库
python init_database.py --recreate-vs
```

启动前，确保已经按照参数配置正确配置各 config 模块。

一键启动

```sh
python startup.py -a
```

## 报错

langchain-core cannot import name 'tracing_enabled'

```sh
pip freeze | grep langchain
pip install --upgrade langchain
```

解决 [langchain-core cannot import name 'tracing_enabled' #15491](https://github.com/langchain-ai/langchain/issues/15491)

## Source Link

---

- [chatchat-space/Langchain-Chatchat](https://github.com/chatchat-space/Langchain-Chatchat)
