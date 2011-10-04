FileUploadResult
========

 `FileUploadResult` オブジェクトは FileTranserの'upload'メソッド成功時のコールバック関数のパラメータに渡されるオブジェクトです。

プロパティ
----------

- __bytesSent:__ アップロードによって送信されたバイト数 (long)
- __responseCode:__ サーバから返されたHTTPレスポンスコード (long)
- __response:__ サーバから送られるHTTPレスポンス (DOMString)

概要
-----------

`FileUploadResult` オブジェクトは `FileTransfer` オブジェクトの `upload` メソッド成功時のコールバック関数に渡されるオブジェクトです。

iOSに関する注意点
----------
- iOSにおける `FileUploadResult` オブジェクトは'responseCode'と'bytesSent'プロパティを持ちません。

