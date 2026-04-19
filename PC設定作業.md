# GitHub 開発環境セットアップ 作業記録

作業日: 2026年04月19日  
環境: Windows（将来的にMacも使用予定）

---

## 午前中の作業

### 1. インストールしたソフトウェア

- **Git for Windows 2.53.0(3) x64**  
  公式サイト git-scm.com からダウンロード・インストール  
  Git Bash も同時にインストールされる

- **Windows Terminal**  
  Microsoft Store からインストール  
  設定から Git Bash プロファイルを手動追加  
  コマンドライン: `C:\Program Files\Git\bin\bash.exe`

- **PowerShell（最新版）**  
  Windows Terminal の案内に従いインストール

---

### 2. SSH鍵の設定

SSH鍵とは、パスワードの代わりに使うデジタルの合鍵。  
秘密鍵（PC上）と公開鍵（GitHub登録）の2つがペアになっており、毎回パスワードを入力せず安全に接続できる。

```bash
ssh-keygen -t ed25519 -C "haku3wabi3@gmail.com"
```

| ファイル | 保存場所 |
|------|------|
| 秘密鍵 | `C:\Users\daiki\.ssh\id_ed25519` |
| 公開鍵 | `C:\Users\daiki\.ssh\id_ed25519.pub` |

---

### 3. GitHubへの公開鍵登録

1. github.com → Settings → SSH and GPG keys を開く
2. "New SSH key" をクリック
3. Title: "Windows PC" と入力
4. Key: 公開鍵の内容を貼り付けて "Add SSH key" をクリック

---

### 4. 接続テスト — 成功 ✅

```bash
ssh -T git@github.com
# 結果: Hi haku3wabi3-hash! You've successfully authenticated
```

---

## 午後の作業

### 5. git config の設定

```bash
git config --global user.name "Takahiro Nakashima"
git config --global user.email "haku3wabi3@gmail.com"
git config --list
# user.name=Takahiro Nakashima
# user.email=haku3wabi3@gmail.com
```

---

### 6. 最初のリポジトリ作成 & push

```bash
mkdir hello-git
cd hello-git
git init
echo "# hello-git" >> README.md
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:haku3wabi3-hash/hello-git.git
git push -u origin main
```

GitHubリポジトリ: https://github.com/haku3wabi3-hash/hello-git

---

### 7. VS Code + GitHub連携

- Visual Studio Code インストール済み
- 拡張機能「GitHub Pull Requests」をインストール
- GitHubアカウント（haku3wabi3-hash）でサインイン
- リポジトリ `hello-git` との連携を確認 ✅

---

## 今後の予定

- [ ] ポートフォリオ用リポジトリの構成を整える
- [ ] Macでも同じ手順でSSH鍵を再設定する

---

お疲れ様でした！GitHub連携の基盤が完成しました 🎉
