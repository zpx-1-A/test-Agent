# test-Agent

本仓库作为 DeepSeek Harness 的默认工作目录（workspace）使用。

- 仓库地址：https://github.com/zpx-1-A/test-Agent.git
- 默认分支：`main`

## 说明

当前为空仓库的初始化提交，用于建立 `main` 分支。后续的项目代码、文档和实验内容都会提交到这里。

## 本地环境说明

本机环境有两个与默认配置不同的地方，换机器或重装后需要重新确认：

1. **git 不在 PATH 中**，需使用完整路径调用：
   `C:\Program Files\Git\cmd\git.exe`
2. **schannel TLS 后端不可用**（握手报 `SEC_E_NO_CREDENTIALS`），因此本仓库已设置
   `http.sslBackend=openssl`。该配置是仓库级的，不要覆盖；如需全局可用，可执行
   `git config --global http.sslBackend openssl`。

推送凭证尚未配置，推送到远端前需要先在凭据库中存入 GitHub 凭据。
