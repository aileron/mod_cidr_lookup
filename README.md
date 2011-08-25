
モバイルサイト作成の際に、IPアドレスによる振り分けを行う目的の為に作成しました

* summary
mod_cidr_lookupは、アクセスしてきたクライアントのIPアドレスが
起動時に読み込んでおいたCIDRブロック群のいずれかにマッチするかどうかを
判別するためのモジュールです。
Apache 2.2系 (FreeBSD) にて 開発および動作実績が有ります。 
マッチした結果は、環境変数 (X_CLIENT_TYPE) とHTTPリクエストヘッダ (X-Client-Type) にセットするので
Apache自身とバックエンドのWebアプリの両方で
同じ情報を参照することができます。

* install
sudo、wget、apxsがコマンドが使用可能な環境での豪快なインストール方法

wget http://aileron.cc/mod_cidr_lookup.c
sudo apxs -c -i -a mod_cidr_lookup.c

httpd.confに帯域ファイルへのパスを追加(絶対パス) 
CIDRFile /usr/local/etc/apache22/cidr.txt

再起動
sudo apacectl restart
