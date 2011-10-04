CaptureVideoOptions
===================

> ビデオキャプチャのオプション設定の情報をカプセル化したオブジェクトです。

プロパティ
----------

- __limit:__ 一度のキャプチャセッションで録音できるビデオクリップの最大数 (デフォルト: 1)
- __duration:__ ビデオクリップの録音最大秒数
- __mode:__ 選択されたオーディオモード。 `capture.supportedVideoModes` で定義されたいずれかの値にマッチしなければならない。

使用例
-------------

    // limit capture operation to 3 video clips
    var options = { limit: 3 };

    navigator.device.capture.captureVideo(captureSuccess, captureError, options);

Androidに関する注意点
--------------

- __duration__ はサポートされていません。レコード秒数はプログラムからは制御できません。
- __mode__ はサポートされていません。ビデオの録音フォーマットはプログラムからは変更できません。録音は3GPP(audio/3gpp)フォーマットで行われます。


BlackBerry WebWorksに関する注意点
--------------------------

- __duration__ はサポートされていません。レコード秒数はプログラムからは制御できません。
- __mode__ はサポートされていません。ビデオの録音フォーマットはプログラムからは変更できません。録音は3GPP(audio/3gpp)フォーマットで行われます。

iOSに関する注意点
--------------------

- __limit__ はサポートされていません。一度の録音で一回のレコードのみ可能です。
- __duration__ はサポートされていません。レコード秒数はプログラムからは制御できません。
- __mode__ はサポートされていません。ビデオの録音フォーマットはプログラムからは変更できません。録音はMOV(audio/quicktime)フォーマットで行われます。

