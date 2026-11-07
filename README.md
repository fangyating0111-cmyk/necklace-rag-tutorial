# 用《项链》学习 RAG

面向初学者的中文 Notebook，展示：
读取原文 → 切分片段 → 向量化 → Chroma 检索 → 生成回答 → 核对引用。

## 文件说明

- 项链_RAG教学.ipynb：教学代码与说明
- 项链.txt：教学使用的原文
- requirements.txt：Python 依赖

## 安装环境

在 Anaconda Prompt 中执行：

```shell
conda create -n rag python=3.11 pip -y
conda activate rag
python -m pip install -r requirements.txt
```

## 运行教学

1. 下载仓库并解压，或克隆仓库。
2. 用 VS Code 打开仓库文件夹，安装 Python 和 Jupyter 扩展。
3. 打开 Notebook，选择 rag 环境作为内核。
4. 确保 Notebook 与项链.txt 在同一目录，从头依次运行单元格。

## 模型说明

- BAAI/bge-small-zh-v1.5：在本机 CPU 上将文本转换成向量，首次运行需要联网下载模型。
- DeepSeek：根据检索片段生成答案，需要自行准备有效 API Key。

在配置单元中设置生成服务：

```python
BASE_URL = "https://api.deepseek.com"
LLM_MODEL = "deepseek-flash"
```

运行生成单元时，按提示隐藏输入密钥。
不要把真实密钥写入代码或上传到 GitHub。

## 对照实验

TOP_K 控制返回的片段数量。

- RUN_GENERATION=False：只展示检索证据和提示词。
- RUN_GENERATION=True：分别生成两轮答案，会调用两次模型接口。

引用检查只核对片段编号。

本地向量数据库会保存在 _chroma 文件夹，无需上传。
