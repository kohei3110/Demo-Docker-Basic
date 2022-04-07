## デモ前

```
# VS Code 起動
cd vscode-remote-try-java
code .
```

## デモ

```
# `.devcontainer/Dockerfile`、`.devcontainer/devcontainer.json` を見せる
# 接続ユーザーを確認( vscode が出力される)
whoami

# java バージョン確認(11.0.14 LTS が出力される)
java -version

# 環境変数確認
echo $JAVA_HOME

# Git 拡張機能がインストールされていることを確認
git --version
```