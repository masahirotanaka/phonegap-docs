Media
=====

> `Media` オブジェクトはオーディオファイルの再生や停止手段を提供します。

    var media = new Media(src, mediaSuccess, [mediaError], [mediaStatus]);


Note: 現在のメディアキャプチャの実装はW3Cの仕様に準拠していません。将来的にはW3Cの仕様に添ったAPIが実装され、このAPIは廃止されます。

パラメータ
----------

- __src__: オーディオコンテンツを示すURI _(DOMString)_
- __mediaSuccess__: (Optional) メディアに関するメソッドの成功時のコールバック関数 _(Function)_
- __mediaError__: (Optional) メディアに関するメソッドの失敗時のコールバック関数 _(Function)_
- __mediaStatus__: (Optional) オーディオのステータスが変化した際に呼び出される関数 _(Function)_

メソッド
-------

- media.getCurrentPosition: 現在のオーディオの再生位置を返します。
- media.getDuration: オーディオの再生時間を返します。
- media.play: オーディオを再生します。
- media.pause: オーディオを一時停止します。
- media.release: OSのオーディオリソースを解放します。
- media.seekTo: オーディオの再生位置を移動します。
- media.startRecord: 録音を開始します。
- media.stopRecord: 録音を停止します。
- media.stop: オーディオの再生を停止します。Stop playing audio file.

読み込み専用パラメータ
---------------------

- ___position__: オーディオの現在の再生位置(秒数)。再生中は自動に更新されないため、 `getCurrentPosition` を用いて更新する。
- ___duration__: 再生時間を秒数で返します。

サポートされているプラットフォーム
-------------------

- Android
- iOS

