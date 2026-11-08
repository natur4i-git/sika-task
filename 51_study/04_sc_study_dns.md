# DNSレコードの記載方法

DNSレコードは、ドメイン名に対してIPアドレスやメールサーバーなどの情報を対応付ける設定情報。

## 1. 主なDNSレコード一覧

| レコード | 記載形式（例） | 用途 |
|---|---|---|
| A | `example.com. IN A 192.0.2.1` | ドメイン名にIPv4アドレスを対応付ける |
| AAAA | `example.com. IN AAAA 2001:db8::1` | ドメイン名にIPv6アドレスを対応付ける |
| CNAME | `www.example.com. IN CNAME example.com.` | 別のドメイン名への別名を設定する |
| MX | `example.com. IN MX 10 mail.example.com.` | メールの配送先メールサーバーを指定する |
| NS | `example.com. IN NS ns1.example.com.` | ドメインを管理するDNSサーバーを指定する |
| PTR | `1.2.0.192.in-addr.arpa. IN PTR example.com.` | IPアドレスからドメイン名を逆引きする |
| TXT | `example.com. IN TXT "v=spf1 include:example.net -all"` | 任意のテキスト情報を登録する。SPFやドメイン所有確認などに使う |
| SOA | `example.com. IN SOA ns1.example.com. admin.example.com. (...)` | ゾーンの管理情報を定義する |
| SRV | `_sip._tcp.example.com. IN SRV 10 5 5060 sip.example.com.` | サービスの提供先ホストとポート番号を指定する |
| CAA | `example.com. IN CAA 0 issue "letsencrypt.org"` | 証明書を発行できる認証局（CA）を制限する |

※ `IN` はインターネットクラスを表す。末尾の `.` は完全修飾ドメイン名（FQDN）の終端を示す。

## 2. 特に重要なレコードの詳細

### Aレコード・AAAAレコード

ドメイン名とIPアドレスを対応付ける。

```dns
example.com. IN A 192.0.2.1
example.com. IN AAAA 2001:db8::1
```

- A：IPv4アドレス
- AAAA：IPv6アドレス

### CNAMEレコード

あるドメイン名を別のドメイン名の別名として登録する。

```dns
www.example.com. IN CNAME example.com.
```

`www.example.com` にアクセスすると、DNSによって `example.com` の名前解決が行われる。

※ CNAMEを設定した名前には、原則として他の種類のレコードを併存させられない。

### MXレコード

メールを受信するメールサーバーを指定する。

```dns
example.com. IN MX 10 mail.example.com.
```

- `10`：優先度（値が小さいほど優先される）
- `mail.example.com.`：メールサーバーのホスト名

複数のメールサーバーを指定することもできる。

```dns
example.com. IN MX 10 mail1.example.com.
example.com. IN MX 20 mail2.example.com.
```

この場合、通常は優先度10のメールサーバーが優先される。

### NSレコード

そのドメインのDNS情報を管理するネームサーバーを指定する。

```dns
example.com. IN NS ns1.example.com.
example.com. IN NS ns2.example.com.
```

### PTRレコード

IPアドレスからドメイン名を調べる逆引きに使用する。

```dns
1.2.0.192.in-addr.arpa. IN PTR example.com.
```

IPv4アドレス `192.0.2.1` を逆引きする場合、IPアドレスの各オクテットを逆順に並べて `in-addr.arpa` を付ける。

### TXTレコード

ドメインに任意のテキスト情報を登録する。

```dns
example.com. IN TXT "v=spf1 include:example.net -all"
```

主な用途：
- SPF：メール送信を許可するサーバーを指定する
- ドメイン所有権の確認
- DMARCなどのメールセキュリティ関連設定

### SOAレコード

DNSゾーンの管理情報を定義する。

```dns
example.com. IN SOA ns1.example.com. admin.example.com. (
    2026110801 ; Serial
    3600       ; Refresh
    600        ; Retry
    86400      ; Expire
    300        ; Minimum
)
```

| 項目 | 意味 |
|---|---|
| MNAME | プライマリDNSサーバー |
| RNAME | 管理者のメールアドレス（表記上の `@` は `.` に置き換える） |
| Serial | ゾーン情報のバージョン番号 |
| Refresh | セカンダリDNSが更新を確認する間隔 |
| Retry | 更新確認に失敗した場合の再試行間隔 |
| Expire | 更新確認ができない状態でゾーン情報を保持する期限 |
| Minimum | 負の応答などに関係するキャッシュ時間の指定 |

## 3. 試験対策の覚え方

| レコード | 覚え方 |
|---|---|
| A | IPv4アドレス |
| AAAA | IPv6アドレス |
| CNAME | 別名 |
| MX | メール配送先 |
| NS | DNSサーバー |
| PTR | IPアドレスの逆引き |
| TXT | テキスト情報・SPF |
| SOA | ゾーンの管理情報 |
| SRV | サービスの接続先・ポート番号 |
| CAA | 証明書発行を許可するCA |

**特に重要なのは A・AAAA・CNAME・MX・NS・PTR・TXT・SOA。**

DNSレコードの問題では、何を対応付けるレコードなのかを理解しておくと判断しやすい。
