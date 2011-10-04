MediaFileData
=============

> メディアファイルのフォーマット情報をカプセル化したオブジェクトです。

プロパティ
----------

- __codecs:__ オーディオ/ビデオで実際に使われているフォーマット (DOMString)
- __bitrate:__ コンテンツのビットレートの平均。画像の場合は常に'0'を値として持つ。 (Number)
- __height:__ 画像/ビデオの縦幅(ピクセル) サウンドクリップの場合は常に'0'を値として持つ。(Number)
- __width:__ 画像/ビデオの横幅(ピクセル) サウンドクリップの場合は常に'0'を値として持つ。 (Number)
- __duration:__ ビデオ/サウンドクリップの再生秒数。画像の場合は常に'0'を値として持つ。(Number)

BlackBerry WebWorksに関する注意点
--------------------------
BlackBerry
BlackBerryではメディアファイルのフォーマットに関する情報を提供するAPIはありません。従って、'MediaFileData'オブジェクトは常に次のデフォルトの値を返します:

- __codecs:__ サポートされていません。常に'null'を返します。
- __bitrate:__ サポートされていません。常に'0'を返します。
- __height:__ サポートされていません。常に'0'を返します。
- __width:__ サポートされていません。常に'0'を返します。
- __duration:__ サポートされていません。常に'0'を返します。

Androidに関する注意点
--------------
MediaFileDataのサポートは下記の通りになります:

- __codecs:__ サポートされていません。常に'null'を返します。
- __bitrate:__ サポートされていません。常に'0'を返します。
- __height:__ 画像/ビデオファイルのみサポートされています。  
- __width:__ 画像/ビデオファイルのみサポートされています。 
- __duration:__ オーディオ/ビデオファイルのみサポートされています。

iOSに関する注意点
----------
MediaFileDataのサポートは下記の通りになります:

- __codecs:__ サポートされていません。常に'null'を返します。
- __bitrate:__ iOS4デバイスのオーディオのみサポートされています。 画像/ビデオに関しては常に'0'を返します。
- __height:__ 画像/ビデオファイルのみサポートされています。  
- __width:__ 画像/ビデオファイルのみサポートされています。 
- __duration:__ オーディオ/ビデオファイルのみサポートされています。