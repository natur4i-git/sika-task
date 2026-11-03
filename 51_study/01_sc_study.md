# SC勉強用
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
- 
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
