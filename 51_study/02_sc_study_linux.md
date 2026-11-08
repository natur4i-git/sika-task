# SC勉強用
## Linux
### 基本コマンド
### Q1. curl
<details>
<summary>答えを見る</summary>

ファイルのアップロード・ダウンロードを行う。

- コマンドの後に引数とURLを指定する。

</details>

### Q2. iptables
<details>
<summary>答えを見る</summary>

ファイアウォール（FW）の設定を行う。

- IPアドレス、ポート番号などを指定する。

</details>

### Q3. ifconfig
<details>
<summary>答えを見る</summary>

PCのIPアドレス、MACアドレスなどを取得・設定する。

</details>

### Q4. top
<details>
<summary>答えを見る</summary>

稼働中のプロセスの状態を表示する。

- `/proc/プロセスID` 内の情報などを利用する。
- ライブラリ関数を通じてプロセス情報を取得する。

**ライブラリ関数とは？**

プログラムで共通して使う処理を部品化したもの。

</details>

### Q5. tar
<details>
<summary>答えを見る</summary>

複数のファイルを1つのアーカイブにまとめる。また、その逆も行える。

</details>

### Q6. cat
<details>
<summary>答えを見る</summary>

ファイルの内容を表示する。

</details>

### Q7. cron
<details>
<summary>答えを見る</summary>

ジョブの実行時間をスケジュール設定する。

</details>

### Q8. route
<details>
<summary>答えを見る</summary>

ルーティング（経路情報）の確認・設定を行う。

</details>

### Q9. ssh
<details>
<summary>答えを見る</summary>

暗号化された通信でリモート接続を行う。

</details>

### Q10. pwd
<details>
<summary>答えを見る</summary>

カレントディレクトリ（現在の作業ディレクトリ）を表示する。

</details>

### Q11. ls
<details>
<summary>答えを見る</summary>

ディレクトリ内のファイルやディレクトリを一覧表示する。

</details>

### Q12. rm
<details>
<summary>答えを見る</summary>

ファイルやディレクトリを削除する。

</details>

### Q13. cp
<details>
<summary>答えを見る</summary>

ファイルやディレクトリをコピーする。

</details>

### Q14. find
<details>
<summary>答えを見る</summary>

ファイルやディレクトリを検索する。

</details>

### Q15. grep
<details>
<summary>答えを見る</summary>

指定したファイルから特定の文字列を検索する。

</details>

### Q16. wget
<details>
<summary>答えを見る</summary>

URLを指定してファイルをダウンロードする。

</details>

## アクセス権限・ユーザー管理

### Q17. chmod
<details>
<summary>答えを見る</summary>

ファイルやディレクトリのアクセス権限（パーミッション）を確認・変更する。

**重要：**

- `664` などの数値表記
- `-rwxrw-r--` などの記号表記
- 所有者・グループ・その他のユーザーの権限

これらを説明できるようにする。

</details>

### Q18. chown
<details>
<summary>答えを見る</summary>

ファイルやディレクトリの所有者を変更する。

```bash
chown ユーザ名 ファイル名
```

</details>

### Q19. chgrp
<details>
<summary>答えを見る</summary>

ファイルやディレクトリの所有グループを変更する。

```bash
chgrp グループ名 ファイル名
```

</details>

### Q20. nohup
<details>
<summary>答えを見る</summary>

ログアウト後も処理を継続できるようにコマンドを実行する。

</details>

## 応用・コマンドの使い方

### Q21. プロキシ経由でサイトにアクセスするcurlコマンドは？

<details>
<summary>答えを見る</summary>

```bash
curl サイトのURL -x プロキシのURL
```

または

```bash
curl サイトのURL --proxy プロキシのURL
```

</details>

### Q22. top以外でプロセスを確認するコマンドは？

<details>
<summary>答えを見る</summary>

```bash
ps
```

</details>

## Linuxのroot権限と一般権限

Linuxでは、ユーザーの権限によって操作できる範囲が異なる。

最大の違いは、**操作できる範囲の広さとシステムへの影響力**である。

## 1. root権限と一般権限の違い

| 項目 | root権限（スーパーユーザー） | 一般権限（一般ユーザー） |
|---|---|---|
| 役割・立場 | システム全体の管理者 | 日常的な作業を行う利用者 |
| 操作できる範囲 | 原則としてシステム全体のファイルや設定を操作できる | 自分に許可された範囲のみ操作できる |
| プロンプトの記号 | `#`（例：`root@host:~#`） | `$`（例：`user@host:~$`） |
| Windowsでの相当機能 | Administrator（管理者）権限に近い | 標準ユーザーに近い |
| 主なリスク | 誤操作によってOS全体に重大な影響を与える可能性がある | 原則として操作できる範囲が制限されている |

※ プロンプト末尾の `#` と `$` は慣例的な目印であり、必ずしも権限を保証するものではない。

## 2. 具体的にできること

### root権限でできること

- すべてのユーザーの作成・削除・パスワード変更
- システム全体のソフトウェアのインストール・削除
- `/etc/` などのシステム設定ファイルの編集
- 他のユーザーのファイルの閲覧・変更
- システム全体の停止・再起動
- ハードウェアやシステムサービスの制御

### 一般権限でできること

- 自分のホームディレクトリ（`/home/ユーザー名/`）内のファイル作成・編集・削除
- 自分に読み書き権限が与えられたファイルの操作
- 一般的なアプリケーションの実行
- 許可された範囲内でのコマンド実行

## 3. root権限への切り替え

一般ユーザーでも、管理者権限が必要な操作を行う場合は、`sudo` コマンドなどを使って一時的にroot権限でコマンドを実行できる。

```bash
sudo apt install パッケージ名
```

この例では、パッケージのインストール処理を管理者権限で実行する。

## 4. 試験対策ポイント

- **root** はLinuxにおけるスーパーユーザーであり、システム全体を管理できる。
- 一般ユーザーは、ファイルやコマンドに設定されたアクセス権限の範囲内で操作する。
- `sudo` を使うと、許可された一般ユーザーが管理者権限でコマンドを実行できる。
- root権限での誤操作は、システム全体に影響する可能性があるため、必要な場合に限って使用する。

**覚え方：rootはシステム全体を操作できる管理者、一般ユーザーは許可された範囲で操作する利用者。**
