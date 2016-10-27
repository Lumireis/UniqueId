# UniqueId
JAVAにてユニークIDを生成するクラスです。
絶対に重複しない一意なIDを最大で１秒間に１０００個発行することが出来ます。
また、ユーザーIDと投稿IDなど、それぞれ用途が違えば重複してもいいというなら違うインスタンスを生成することで対応可能です。

# 発行されるIDの形式
データ型　long
最大桁数　17桁
数値は発行された日時を示します。

２０１６年１０月２７日１５時０３分１２秒に発行した場合
20161027150312000
がIDとして生成されます。

また、同じ秒である　２０１６年１０月２７日１５時０３分１２秒に２回目の発行を行った場合
20161027150312001
がIDとして生成され、このように下３桁は同じ日時秒での連番を返します。

そのため、最大で１秒間に１０００個のIDを発行できることになりますが、仮にそれ以上のIDをが発行しようとした場合スレッドはブロックされます。
（秒が切り替わるまで）

# 注意点
サーバーの稼働時間がコロコロ変わるシステムでは利用できません。
また、このライブラリを使用したプログラム実行中にサーバー時間が変わった場合、変わった時間だけスレッドがブロックされる可能性があります。
