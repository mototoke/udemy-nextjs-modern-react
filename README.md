# udemy-nextjs-modern-react

## 開発環境起動
```
# コマンドプロンプト or powershellにて↓のコマンドを実行
docker-compose -f docker-compose.dev.yml build
docker-compose -f docker-compose.dev.yml up -d
```

## 環境構築
### Docker for windowsのインストール
wsl内のdockerだけで開発出来ると思っていましたが
windows for Dockerがないとremote-containerが使えない？かもしれません。
https://docs.docker.jp/docker-for-windows/install.html
https://docs.docker.com/desktop/windows/install/

## 環境構築
### WSLのインストール
[wsl install](https://docs.microsoft.com/ja-jp/windows/wsl/install)に従ってWSLをインストールする

管理者の PowerShell または Windows コマンド プロンプトに次のコマンドを入力し、PCを再起動する。

```PowerShell
wsl --install
```

再起動後、wslのインストール完了してイカのコマンドを実行
```
wsl -l -v

C:\Users\<UserName>>wsl -l -v
  NAME      STATE           VERSION
* Ubuntu    Stopped         2
```

- wslの起動
管理者で起動したコマンドプロンプト or Poweshellにて
```
wsl
```

### Dockerのインストール

```shell
# パッケージを更新
sudo apt-get update -y
sudo apt-get upgrade -y

# Dockerのインストールに必要なパッケージをインストールする
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y

# DockerのGPG鍵を登録する
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# DockerのPPAを登録する
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Dockerのインストール
sudo apt-get update -y
sudo apt-get install docker-ce docker-ce-cli containerd.io -y

# sudoなしでdockerコマンドを使えるようにする
sudo usermod -aG docker $USER

# ここまでで一旦シェルを抜けます
exit
```

dockerインストールの確認
```
# 管理者権限のコマンドプロンプト or poweshellにて
wsl

# wslにて
<UserName>@XXXXX-XXXXX:/mnt/c/WINDOWS/system32$  docker -v
Docker version 20.10.12, build e91ed57
```

### dockerの起動

```shell
sudo service docker start
```

### docker-composeのインストール
https://docs.docker.com/compose/install/
```shell
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

docker-compose --version
> docker-compose version 1.29.2, build 5becea4c
```
