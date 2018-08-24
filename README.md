# local_vagrant-docker_environment
すぐに使えるローカルWEB開発環境を構築する

## 内容
- vagrant up とdocker-compose up のみで環境構築
- ubuntu-16.04 + PHP7 + nginx (vagrant, docker)

  - vagrant provisioning を利用し、仮想環境構築時にdockerとdocker-composeのインストールを自動的に行う
  - クライアントPCに依存しない、定常的なローカル開発環境を構築する
  - 構築する環境は要件によって変わるため、ubuntu上で phpfpm + nginx が動作する環境をスケルトンとして構築する
  
## フォルダ構成

```
.
├── project
│   ├── app　アプリケーションの配置場所
│   │   └── index.php
│   ├── docker　dockerの各コンテナの設定ファイル
│   │   ├── nginx
│   │   │   ├── Dockerfile
│   │   │   └── server.conf
│   │   └── php7-fpm
│   │       └── Dockerfile
│   └── docker-compose.yml　docker-compose の設定ファイル
├── README.md
└── Vagrantfile　vagrant の設定ファイル

```

## 動作環境
- vagrantのインストール

> https://www.vagrantup.com/

windowsの場合は、仮想環境に接続するために
TeraTerm、puttyなどのsshクライアントをインストールしておく


## 使い方

### 以下のコマンドを実行する

```bash
$ vagrant up
$ vagrant ssh
$ cd /vagrant/project
$ docker-compose up

```

- windowsの場合は `vagrant ssh`　の代わりにsshクライアントで接続し、3行目以下のコマンドを実行する。
- IPはvagrantfileを書き換えてない場合は、192.168.33.177

### dev.local にブラウザで接続し、phpinfoの設定画面が出力されることを確認する。

http://dev.local