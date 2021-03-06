# セットアップ

## 必要なもの

- (Windows の人は) Windows Subsystem for Linux
  - ディストリビューションは Ubuntu がよさそう
- VS Code
  - 拡張機能
    - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
    - [Prettier \- Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- Node.js
- yarn

## インストール

インストールされているかの確認と、されていなかった場合のインストール方法です。

### Windows Subsystem for Linux

[Windows 10 に WSL をインストールする \| Microsoft Docs](https://docs.microsoft.com/ja-jp/windows/wsl/install-win10) をご覧ください。

### VS Code

---

**Note:** Windows の人は WSL ではなく Windows に VS Code をインストールして、[Remote - WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) 拡張機能をインストールしてください。
詳しくは [WSL で VS Code の使用を開始する \| Microsoft Docs](https://docs.microsoft.com/ja-jp/windows/wsl/tutorials/wsl-vscode) や [【WSL / WSL2】VSCode×WSL で Windows 上に Linux 開発環境を構築 \- Qiita](https://qiita.com/_masa_u/items/d3c1fa7898b0783bc3ed) をご覧ください。

---

#### 起動方法

各 OS のアプリ一覧から VS Code を探して起動します。

#### インストール方法

[Visual Studio Code 公式サイト](https://code.visualstudio.com/) から、ダウンロードしてインストールします。

例として、 Ubuntu でのインストール方法を下記に示します。

```bash
sudo apt install ダウンロードされた.debファイル
```

また、以下の 2 つの拡張機能をインストールしてください。

- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
- [Prettier \- Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

拡張機能の管理画面は、下図のように、VS Code のウィンドウの左側にあるアイコンから開けます。

![拡張機能のインストール画面](./img/00-setup/ext.png)

### Node.js

#### インストールされているバージョンの確認方法

```bash
node -v
```

`v16.7.0` のように表示されれば OK です。

`node` コマンドが見つからない旨のエラーメッセージが表示された場合は、Node.js がインストールされていません。
下記インストール方法を参照し、インストールしてください。

`v14.0.0` 未満のバージョンが表示された場合は更新が必要です。
インストールされた方法に応じて、更新するか、アンインストールして下記インストール方法でインストールするなどをしてください。

---

**Note:** Node.js をインストールした方法がわからない場合は以下のコマンドを実行してください。
このコマンドは、`node` コマンドの実行ファイルがどこのフォルダにあるかを確認するコマンドです。

```sh
which node
```

例えば、Nodeenv でインストールした場合は `ホームディレクトリ/.nodenv/bin/node` 、Nodebrew でインストールした人は `ホームディレクトリ/.nodebrew/current/bin/node` のように表示されます。

---

#### インストール方法

Node.js には、以下のようなインストール方法があります。
バージョンマネージャは、マシンに複数のバージョンの Node.js をインストールしてプロジェクトによって使用するバージョンを変えるなど、
柔軟に複数の Node.js のバージョンを管理することができるソフトウェアです。
Python の pyenv、Ruby の rbenv など、様々な言語で同様の仕組みはあります。

- [Node.js 公式サイト](https://nodejs.org/ja/) から実行ファイルをダウンロードしてインストールする方法
- Node.js のバージョンマネージャを使用しインストールする方法
  - [nvm](https://github.com/nvm-sh/nvm)
    - Windows を使用する場合は、WSL を使用するか [nvm-windows](https://github.com/coreybutler/nvm-windows) を使用する必要があるそうです
  - [nodenv](https://github.com/nodenv/nodenv)
    - Windows を使用する場合は、WSL を使用する必要があるそうです
  - [n](https://github.com/tj/n)
    - Windows を使用する場合は、WSL を使用する必要があるそうです
  - [Volta](https://volta.sh/)

ここでは、nvm を使用して Node.js をインストールします。
これは、[WSL 2 上で Node\.jis を設定する \| Microsoft Docs](https://docs.microsoft.com/ja-jp/windows/dev-environment/javascript/nodejs-on-wsl) や、後述する [Create React App の公式ドキュメント](https://create-react-app.dev/docs/getting-started#creating-an-app) で紹介されているなど、広く使われているからです。

[nvm の Install & Update Script](https://github.com/nvm-sh/nvm#install--update-script) を実行し、`nvm install node --lts` を実行することで、Node.js の最新 LTS 版がインストールされます。

インストールできたら、もう一度「インストールされているバージョンの確認方法」を実行し、インストールできていることを確認しましょう。

### yarn

#### インストールされているバージョンの確認方法

```bash
yarn -v
```

`v1.22.5` のように表示されれば OK です。

#### インストール

下記のコマンドでインストールできます。
また、すでにインストールしていた人も、下記のコマンドで更新できます。

```bash
npm install --global yarn
```

## 環境構築の確認

最後に、環境構築ができているか確認してみましょう。

---

**注意:** WSL で開発する場合は、以降の作業を Windows 側のファイルシステムではなく、 WSL 側のファイルシステムで行うようにしてください。
開発時にソフトウェアの動作が不安定になる事例が確認されています。

---

この項目では、[Create React App](https://create-react-app.dev/) を使用します。
これは、 React を動かすために必要なファイルや依存ソフトウェアといった環境を準備してくれるものです。

普段プログラムを置いているディレクトリ (筆者は `~/Project` です) で、以下のコマンドを実行してください。

```sh
yarn create react-app my-app --template typescript
```

コマンドが成功すると、`my-app` というフォルダができています。

`my-app` を VS Code で開くか、`cd my-app` でカレントディレクトリを移動し、下記コマンドを実行してください。

```sh
yarn start
```

http://localhost:3000/ がブラウザで開かれ、このような画面が表示されると環境構築が完了しています。

![Create React App の実行結果。React のロゴが表示されている](img/00-setup/create-react-app.png)

## まとめ

このセクションでは、環境構築の方法について説明しました。

後のセクションをやっていく上で、うまく動かないなどの問題があれば、このセクションを見返してみてください。
