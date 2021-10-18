# IDE

## VS_CODE

> 服务端手工安装 vs-code-server 服务 [参考](https://stackoverflow.com/questions/56671520/how-can-i-install-vscode-server-in-linux-offline)

``` shell
# 1.First get commit id
commit_id=c13f1abb110fc756f9b3a6f16670df9cd9d4cf63 # 需自行替换 commit_id

# 2. Download url is: https://update.code.visualstudio.com/commit:${commit_id}/server-linux-x64/stable
curl -sSL "https://update.code.visualstudio.com/commit:${commit_id}/server-linux-x64/stable" -o vscode-server-linux-x64.tar.gz
# curl -sSL "https://update.code.visualstudio.com/commit:${commit_id}/server-linux-x64/stable/vscode-server-linux-x64.tar.gz" -o vscode-server-linux-x64.tar.gz

# 3. ensure the forlder
mkdir -p ~/.vscode-server/bin/${commit_id}
# 4. Unzip the downloaded vscode-server-linux-x64.tar.gz to ~/.vscode-server/bin/${commit_id} without vscode-server-linux-x64 dir
tar zxvf /tmp/vscode-server-linux-x64.tar.gz -C ~/.vscode-server/bin/${commit_id} --strip 1
# 5. Create 0 file under ~/.vscode-server/bin/${commit_id}
touch ~/.vscode-server/bin/${commit_id}/0
```