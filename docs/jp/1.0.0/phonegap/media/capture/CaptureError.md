CaptureError
============

> メディアのキャプチャに失敗した場合のエラーコードをカプセル化したオブジェクトです。

プロパティ
----------

- __code:__ 下記のエラーコードが格納されます。

定数
---------

- CaptureError.`CAPTURE_INTERNAL_ERR`: カメラ/マイクが画像/音声のキャプチャに失敗したことを表します。
- CaptureError.`CAPTURE_APPLICATION_BUSY`: カメラ/オーディオアプリがビジーであることを表します。
- CaptureError.`CAPTURE_INVALID_ARGUMENT`: APIの不正な使用を表します。
- CaptureError.`CAPTURE_NO_MEDIA_FILES`: ユーザがキャプチャする前の段階でカメラ/オーディオアプリを終了させたことを表します。
- CaptureError.`CAPTURE_NOT_SUPPORTED`: 要求されたキャプチャ操作がサポートされていないことを表します。
