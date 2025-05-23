# Git初期設定・VSCodeとGitHub連携手順（Windows/Mac/Ubuntu対応）

---

## 1. Gitのインストール

### Windows
1. [Git公式サイト](https://git-scm.com/)からインストーラーをダウンロード
2. インストーラーを実行し、画面の指示に従ってインストール

### Mac
```sh
brew install git
```
または、Xcodeコマンドラインツールをインストール（`git`コマンド実行時に案内あり）

### Ubuntu
```sh
sudo apt update
sudo apt install git
```

---

## 2. Gitの初期設定

全OS共通。ターミナルで以下を実行：

```sh
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
git config --global core.editor "code --wait"
```

---

## 3. GitHubアカウント作成・ログイン

1. [GitHub](https://github.com/)でアカウントを作成
2. 必要に応じてメール認証

---

## 4. GitHubのno-replyメールアドレスの確認

1. GitHubにログイン後、右上のプロフィールアイコンをクリック
2. 「Settings」を選択
3. 左メニューから「Emails」を選択
4. 「Keep my email address private」が有効になっている場合、`ID+ユーザー名@users.noreply.github.com` の形式のメールアドレスが表示されます
5. このメールアドレスをコピーして、Gitの設定で使用できます

> **Note**  
> プライバシー設定で「Keep my email address private」を有効にすると、GitHubはこのno-replyメールアドレスをコミットの作者として使用します。

---

## 5. SSHキーの作成とGitHubへの登録


### Windows
1. 「Git Bash」または「PowerShell」で以下を実行：
    ```sh
    ssh-keygen -t ed25519 -C "あなたのメールアドレス"
    ```
2. デフォルトの保存場所でOK。パスフレーズは任意。
3. 公開鍵の内容をコピー：
    ```sh
    # PowerShellの場合
    Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub

    # コマンドプロンプトの場合
    type %USERPROFILE%\.ssh\id_ed25519.pub
    ```

### Mac/Ubuntu
1. ターミナルで以下を実行：
    ```sh
    ssh-keygen -t ed25519 -C "あなたのメールアドレス"
    ```
2. デフォルトの保存場所でOK。パスフレーズは任意。
3. 公開鍵の内容をコピー：
    ```sh
    cat ~/.ssh/id_ed25519.pub
    ```

#### GitHubへの登録（全OS共通）
1. GitHubの「Settings」→「SSH and GPG keys」→「New SSH key」
2. コピーした公開鍵を貼り付けて登録

---

## 5. VSCodeとGitHubの連携

### 拡張機能のインストール（全OS共通）
- VSCode左側の拡張機能アイコンから「GitHub Pull Requests and Issues」をインストール

### サインイン（全OS共通）
1. VSCode左下の「アカウント」アイコン → 「GitHubでサインイン」
2. ブラウザが開くので、GitHubで認証

---

## 6. リポジトリのクローン

VSCodeのコマンドパレット（`Ctrl+Shift+P`または`Cmd+Shift+P`）で  
`Git: Clone` を選択し、リポジトリURLを入力

---

## 7. よく使うGitコマンド

```sh
git status         # 状態確認
git add .          # 変更をステージ
git commit -m "コメント" # コミット
git push           # リモートに反映
git pull           # 最新を取得
```

---

## 参考

- [Git公式ドキュメント](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/ja)
- [VSCode公式Git連携](https://code.visualstudio.com/docs/editor/versioncontrol)

---