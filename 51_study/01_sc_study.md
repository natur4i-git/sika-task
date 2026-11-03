# SC勉強用
## HTTPとCOOKIE
### COOKIE
- Secure：HTTPS通信下でのみCookieを送信する。通信経路での盗聴を防ぎやすくする。
- HttpOnly：JavaScriptなどからCookieにアクセスできなくする。XSSによるCookie窃取対策。
- SameSite：CSRF対策。クロスサイトのリクエストでCookieを送信するかどうかを制御する。Strict、Lax、Noneがある。
- Domain：指定したドメインとそのサブドメインへのリクエストにCookieを送信する。
### HTTP
##### リクエストヘッダ
- X-Forwared-For：送信元のIPアドレスを記載する。ロードバランサーやプロキシサーバーで設定される。

##### レスポンスヘッダ
- X-Frame-Options：指定したページをframeやiframeでページを表示することを拒否する。クリックジャッキング対策
- Content-Security-Policy：読み込み・実行を許可するコンテンツの送信元などを制限する。XSS対策。
- Strict-Transport Security：ブラウザに対して、以降のアクセスをHTTPSに限定するよう指示する。
##### リクエスト時のメッセージボディ
- POST：サーバーに送信する情報が入る
- GET、HEAD：メッセージボディなし
##### レスポンス時のメッセージボディ
- HTML、JSON、XML、画像データなどが入る。
- HEAD、204、304などはボディなし。

##### CSPについて
- 下記のようにdefault-srcはベースラインとして使用できる
```CSP
Content-Security-Policy:
  default-src 'none';//デフォルトで全てのリソースを禁止
  img-src 'self';
  script-src 'self';
  style-src 'self';
```
## ネットワークプロトコル
### ネットワークプロトコル・ポート番号一覧

| プロトコル | ポート番号 | 用途 |
|---|---:|---|
| FTP | 20 / 21 | ファイル転送 |
| SSH | 22 | 暗号化された遠隔ログイン |
| SFTP | 22 | SSHを利用したファイル転送 |
| Telnet | 23 | 暗号化されない遠隔ログイン |
| SMTP | 25 | メール送信・サーバー間転送 |
| DNS | 53 | ドメイン名とIPアドレスの名前解決 |
| DHCP | 67 / 68 | IPアドレスの自動割り当て |
| TFTP | 69 | 簡易ファイル転送 |
| HTTP | 80 | Web通信 |
| POP3 | 110 | メール受信 |
| NTP | 123 | 時刻同期 |
| IMAP4 | 143 | メール受信・サーバー上での管理 |
| SNMP | 161 / 162 | ネットワーク機器の監視・管理 |
| LDAP | 389 | ディレクトリサービス |
| HTTPS | 443 | 暗号化されたWeb通信 |
| IPsec IKE | 500 | IPsecの鍵交換 |
| SMB | 445 | ファイル共有 |
