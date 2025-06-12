+++
title = 'How_to_use_github_actions'
date = 2025-06-12T11:39:54+08:00
draft = false
+++


## 1. 什么是GitHub Actions？

GitHub Actions 是 GitHub 提供的一种持续集成服务，它允许用户在 GitHub 仓库中自动执行一系列的任务，包括编译代码、运行测试、发布软件包、部署应用等。

## 2. 如何使用GitHub Actions？

GitHub Actions 的使用非常简单，只需要在仓库的根目录下创建一个 `.github/workflows` 目录，并在该目录下创建一个 YAML 文件，文件名可以自定义，但必须以 `.yml` 结尾。

下面是一个简单的示例：

```yaml
name: CI

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up Python 3.8
      uses: actions/setup-python@v2
      with:
        python-version: 3.8
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install flake8 pytest
        if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
    - name: Lint with flake8
      run: |
        # stop the build if there are Python syntax errors or undefined names
        flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
        # exit-zero treats all errors as warnings. The GitHub editor is 127 chars wide
        flake8 . --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics
    - name: Test with pytest
      run: |
        pytest
```

该示例包含两个主要部分：

- `name`：自定义工作流名称，用于标识该工作流。
- `on`：定义触发工作流的事件，可以是 `push`、`pull_request`、`release` 等。
- `jobs`：定义工作流的具体任务，可以有多个任务。

每个任务都包含以下三个部分：

- `runs-on`：定义任务运行的环境，可以是 `ubuntu-latest`、`windows-latest`、`macos-latest` 等。
- `steps`：定义任务的具体步骤，可以有多个步骤。
- `name`：自定义步骤名称，用于标识该步骤。

每个步骤都包含以下三个部分：

- `uses`：定义步骤使用的 GitHub Action，可以是官方提供的 Action 或用户自己编写的 Action。
