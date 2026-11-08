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
