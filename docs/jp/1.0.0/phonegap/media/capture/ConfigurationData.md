ConfigurationData
=================

> メディアキャプチャに関するパラメータをカプセル化したオブジェクトです。

概要
-----------

このオブジェクトはデバイスでサポートされているメディアキャプチャのモードを保持しています。'ConfigurationData'は'MEMIタイプ'、ビデオや画像の次元に関する情報を保持しています。 

MIMEタイプは [RFC2046](http://www.ietf.org/rfc/rfc2046.txt) に従ってください。(例:

- video/3gpp
- video/quicktime
- image/jpeg
- audio/amr
- audio/wav 

プロパティ
----------

- __type:__ メディアのタイプを表す半角英数字の文字列 (DOMString)
- __height:__  画像/ビデオの縦幅(ピクセル) サウンドクリップの場合はこのプロパティは'0'を値として持ちます。 (Number)
- __width:__ 画像/ビデオの横幅(ピクセル) サウンドクリップの場合はこのプロパティは'0'を値として持ちます。(Number)

使用例
-------------

    // サポートされている画像のモードを取得
    var imageModes = navigator.device.capture.supportedImageModes;

    // 最も高い解像度を持つモードを取得
    var width = 0;
    var selectedmode;
    for each (var mode in imageModes) {
        if (mode.width > width) {
            width = mode.width;
            selectedmode = mode;
        }
    }


このオブジェクトは現在はどのプラットフォームでもサポートされていません。全ての'ConfigurationData'は空の配列になります。
