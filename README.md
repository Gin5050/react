# react

## 環境構築

anyenvのインストール

```bash
git clone https://github.com/anyenv/anyenv ~/.anyenv
echo 'export PATH="$HOME/.anyenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(anyenv init -)"' >> ~/.bash_profile
exec $SHELL -l
```

nodenvをインストール

```bash
anyenv install nodenv
```

nodenvでnodeをインストール

```bash
nodenv install 12.10.0
```

以下のエラー出現
```bash
yuki@yuki:~$ nodenv install 12.10.0
nodenv: /home/yuki/.anyenv/envs/nodenv/versions/12.10.0 already exists
continue with installation? (y/N) y
Downloading node-v12.10.0-linux-x64.tar.gz...
-> https://nodejs.org/dist/v12.10.0/node-v12.10.0-linux-x64.tar.gz
Installing node-v12.10.0-linux-x64...
Installed node-v12.10.0-linux-x64 to /home/yuki/.anyenv/envs/nodenv/versions/12.10.0

nodenv: default-packages file not found
```

以下で解決

```bash
mkdir -p "$(nodenv root)/plugins"
touch $(nodenv root)/default-packages
```

yarnのインストール

```bash
npm install -g yarn
```

## ReactのHello world

```bash
npx create-react-app hellow-world --typescript
```

hellow-worldというディレクトリが生成される。

そこで下記コマンド実行

```bash
yarn start
```

## Reactアプリケーション作成手順

1. Node.jsインストール
2. プロジェクトのフォルダ名は`react_app`とした
```bash
npx create-react-app <フォルダ名>
```

すると以下のようなコマンドが表示される。

```bash
cd react_app
yarn start
```

`yarn start`を実行するとブラウザで

<img src="../img/readme/yarn_start.png" title="サンプル">

## ReactでTypescript

`create-react-app`はインストール済みとする。
ただし`create-react-app`はグローバルでインストールされてないといけない。

```bash
yarn global add create-react-app
```

で、これだけだとPATHが通ってないので、`.bash_profile`などに以下を追記。

```bash
export PATH="$PATH:`yarn global bin`"
```

これで以下を実行。

```bash
create-react-app ts_react --typescript
```

すると`tsconfig.json`などがある状態でプロジェクトが作成される。