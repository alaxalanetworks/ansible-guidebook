[→目次に戻る](./README.md)

# 付録．TextFSMについて

Ansible 2.4 で Ansible でネットワーク装置のコマンド結果をparseするための parse\_cli\_textfsm というフィルタープラグインが搭載されました。parse\_cli\_textfsm は、テンプレートファイルとネットワーク装置のCLIからのコマンド応答の2つの入力を受け取り、TextFSMというライブラリを呼び出して、さまざまなソースから有用な情報を解析できます。TextFSM を利用するためには、別途TextFSMのインストールとテンプレートファイルを用意する必要があります。
TextFSMはGoogle社で開発され、より広範なコミュニティのためにApache 2.0ライセンスでリリースされました。詳細は [https://github.com/google/textfsm](https://github.com/google/textfsm)　をご参照ください。

- TextFSMのインストール
parse\_cli\_textfsm フィルタープラグインでは、内部で TextFSM を利用しているので、以下方法であらかじめインストールします。
~~~yaml
$ sudo pip install textfsm
~~~

- テンプレートファイルの準備
装置が出力する文字列を正規表現で記述されたテンプレートファイルによって解析し、必要な項目を抽出します。

テンプレートファイル例　(show port)
~~~yaml
$ cat template/alaxala_show_port
Value PORT (\d+/[\d\s]+)
Value NAME (\S+)
Value STATUS (\S+)
Value SPEED (\S+)
Value DUPLEX (\S+)
Value FCTL (\S+)
Value MTU (\S+)
Value CHGR (\S+)

Start
  ^\s${PORT}\s+${NAME}\s+${STATUS}\s+${SPEED}\s+${DUPLEX}\s+${FCTL}\s+${MTU}\s+${CHGR} -> Record
~~~

show port コマンド (AlaxalA装置出力結果)
~~~
# show port 1/0/1
Date 2018/04/05 04:33:16 UTC
Port Counts:  1
Port  Name           Status   Speed           Duplex     FCtl FrLen ChGr/Status
0/ 1 geth1/0/1       up       1000BASE-T      full(auto) off   1568   -/-
~~~

TextFSMの解析実行結果
~~~
 {
            "CHGR": "-/-",
            "DUPLEX": "full(auto)",
            "FCTL": "off",
            "MTU": "1568",
            "NAME": "geth1/0/1",
            "PORT": "0/ 1",
            "SPEED": "1000BASE-T",
            "STATUS": "up"
        }
~~~
正規表現の詳細は、以下のサイトを参照ください。

【python2.7】 [https://docs.python.jp/2.7/library/re.html](https://docs.python.jp/2.7/library/re.html)

【python3.5】 [https://docs.python.jp/3.5/library/re.html](https://docs.python.jp/3.5/library/re.html)

基本的な正規表現の表記例を以下に示します。

- **基本のメタキャラクタ**
メタキャラクタにより、任意の1文字や任意の半角数字などを指定することができます。

|メタキャラクタ | 意味 |
|-----------| -----|
|．         | 任意の1文字 |
|\\s        |空白文字(半角スペース,タブ,改行,キャリッジリターン)|
|\\S        |空白文字以外|
|\\d        |半角数字(0\~9)|
|\\D        |半角数字以外|
|\\b        |単語の境界に一致|

- **量指定子**
量指定子は、文字の後ろに配置し、前の文字が何回出てくるのかを指定します。

|量指定子   |意味  |
|-------- | ----|
| *|    0回以上の繰り返しにマッチ|
|+ |    1回以上の繰り返しにマッチ|
|{n} |  n回の繰り返しにマッチする表現|
|{n,} | n回以上の繰り返しにマッチする表現|
| {n,m}  |     n回以上m回以下の繰り返しにマッチする表現|
| ?  |0回または1回の出現にマッチする表現|

- **アンカー**
文字列の先頭や末尾に特定の文字がある文字列も表現できます。

|量指定子  |  意味  |
|--------| -------|
|^pattern  | 文字列の先頭にpatternがある文字列に一致 |
|pattern\$  | 文字列の末尾にpatternがある文字列に一致 |

[→目次に戻る](./README.md)
