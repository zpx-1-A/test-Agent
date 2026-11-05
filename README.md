# test-Agent

本仓库作为 DeepSeek Harness 的默认工作目录（workspace）使用。

- 仓库地址：https://github.com/zpx-1-A/test-Agent.git
- 默认分支：`main`

## 说明

本仓库用于存放后续的项目代码、文档和实验内容。

## 本地环境说明

本机环境有几处与默认配置不同，换机器或重装后需要重新确认：

1. **git 不在 PATH 中**，需使用完整路径调用：
   `C:\Program Files\Git\cmd\git.exe`
2. **schannel TLS 后端不可用**（握手报 `SEC_E_NO_CREDENTIALS`），因此本仓库已设置
   `http.sslBackend=openssl`。该配置是仓库级的，不要覆盖；如需全局可用，可执行
   `git config --global http.sslBackend openssl`。
3. **网络存在 TLS 中间人拦截**：部分时段访问 github.com 会返回证书主体为 `ruijie`
   的证书，或 DNS 解析到无效地址，表现为 `certificate subject name ... does not match`
   或 `Could not resolve host`。遇到时重试即可，不要关闭 `sslVerify`，否则会把凭证
   暴露给中间人。
4. **凭证通过 remote URL 传递**：`credential.helper` 需要经 `sh` 启动，而沙箱禁止创建
   命名管道，导致助手读取失败；所以 origin 的 URL 中内联了 Token。
   因此**不要在共享日志中执行 `git remote -v`**，它会打印出 Token。

## 凭证

`origin` 的 URL 内联了 GitHub Token，因此本地可以直接 `git push`。
Token 泄露或轮换后，用下面命令更新（把 `<TOKEN>` 换成新 Token）：

```powershell
git remote set-url origin "https://zpx-1-A:<TOKEN>@github.com/zpx-1-A/test-Agent.git"
```
