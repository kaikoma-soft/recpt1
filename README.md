
本プログラムは、[stz2012/recpt1](https://github.com/stz2012/recpt1) のフォークで、
その目的は [raspirec Ver1.3.0](https://github.com/kaikoma-soft/raspirec)
に必要な改造＋おまけを施したものです。

## 変更点は次のものです。

* --sid オプションで、EPGを指定しても、Rescan ID が起きると、それ以降の
   EPGデータが出力されなくなるバグ(?) の修正
* コンパイル時の警告を無くす。
* チャンネル情報の定義部分を別ファイルとし、
  [別ツール]( https://github.com/kaikoma-soft/mkChConvTable )
  で生成したチャンネル情報のファイルを取り込み易くする。

## 履歴

* 2022/03/09
  BSに 下記の 3局追加
```
    BSよしもと     BS23_1
    BSJapanext     BS23_2
    BS松竹東急     BS23_3
```
* 2024/06/08 
```
    NHKBSプレミアム   -> NHK に変更
    スターチャンネル1 -> スターチャンネル に変更
    スターチャンネル2 -> 停波により削除
    スターチャンネル3 -> 停波により削除
    など
```

* 2024/10/09
```
    旧NHKBSプレミアム -> 停波により削除
    ＢＳ釣りビジョン  -> BS11_1 から BS3_2
    ＢＳアニマックス  -> BS13_2 から BS3_1
```

* 2024/11/11
```
    放送大学テレビ -> BS11_2 から BS13_2
```

* 2025/01/11
```
    BSJapanext(BS23_2) -> BS10(BS15_2)           # スロットのずれを補正済み
    スターチャンネル   -> BS10スターch(BS15_1)
```

* 2025/02/28    
    今ままで空きスロットが有っても、ズレが起きなかった下記の２局がずれる
    ようになったので、補正を行うように。
    
```
    ＢＳ１２トゥエルビ  BS9_2  => BS9_1
    ＢＳ松竹東急        BS23_3 => BS23_2
```

* 2025/07/01<br>
  局名変更(名称のみ)
   
```
     BS23_3(BS23_2)    BS松竹東急     -> J：COM BS
     CS_321            スペシャプラス -> MusicJapan
```
## インストール方法

インストール方法は
[下記のスクリプト](https://gist.github.com/kaikoma-soft/252e623b1f8937e8a091dbda9695bed1#file-recpt1_install-sh)
の通りです。(あらかじめ libarib25 がインストールされている事)
```
  % mkdir /tmp/recpt1 ; cd /tmp/recpt1
  % git clone  --depth 1 https://github.com/kaikoma-soft/recpt1.git .
  % cd recpt1
  % ./autogen.sh
  % ./configure --enable-b25
  % make 
  % sudo make install
  % make maintainer-clean
```


## 動作確認環境

動作確認環境は Ubuntu 24.04.1 LTS (6.8.0-49-generic) です。

## オリジナルの README
```
【recpt1 HTTPサーバ版RC4 + α（STZ版）】
Linux用PT1/PT2/PT3録画プログラムです。
こちらは亜流版ですのでご注意下さい。

本家はこちら→ http://hg.honeyplanet.jp/pt1/
※ドライバー部分は本家やその他分家（↓）のものをお使い下さい。
　PT1/PT2：http://sourceforge.jp/projects/pt1dvr/
　PT3：https://github.com/m-tsudo/pt3
※libarib25はこちら→ https://github.com/stz2012/libarib25

cd recpt1/recpt1
./autogen.sh
./configure --enable-b25
make
でビルドした後、
./recpt1 録画するチャンネル 録画秒数 出力先ファイル名
で録画されます。
詳しいオプションはrecpt1 --helpをご覧下さい。

Special Thanks:
・2chの「Linuxでテレビ総合」スレッドの皆様

動作確認環境:
  Debian 11 x86_64 GNU/Linux
  Linux 5.10.0 SMP
  Ubuntu 22.04 LTS x86_64 GNU/Linux
  Linux 5.15.0 SMP
```
