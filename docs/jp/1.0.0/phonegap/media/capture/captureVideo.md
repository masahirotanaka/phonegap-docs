capture.captureVideo
====================

> ビデオレコーダを起動し、レコードしたビデオクリップの情報を返します。

    navigator.device.capture.captureVideo( 
	    CaptureCB captureSuccess, CaptureErrorCB captureError, [CaptureVideoOptions options]
	);

概要
-----------

このメソッドはデバイスのデフォルトのビデオアプリを使って、ビデオレコードを非同期的に開始します。一回のセッションで複数のレコードを行うことができます。

レコード処理はユーザがレコードをキャンセルするか、 __limit__ パラメータで指定されるレコードの最大件数に達した場合に終了します。もし、 __limit__ に値が指定されていない場合はデフォルトとして'1'が使われます。よってこの場合、ユーザが一つの録音を終了した時点でレコードは終了します。

レコード操作が成功し正常に終了した際には、'CaptureCB'コールバックがレコードされたビデオの情報を保持する'MediaFile'オブジェクトを引数に呼び出されます。
もしレコードが完了する前にユーザが処理をキャンセルした場合、`CaptureError.CAPTURE_NO_MEDIA_FILES`を保持する'CaptureError'オブジェクトを引数に'CaptureErrroCB'コールバック関数が呼び出されます。


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

    // 成功時のコールバック
    var captureSuccess = function(mediaFiles) {
        var i, path, len;
        for (i = 0, len = mediaFiles.length; i < len; i += 1) {
            path = mediaFiles[i].fullPath;
            // do something interesting with the file
        }
    };

    // 失敗時のコールバック
    var captureError = function(error) {
        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
    };

    // ビデオのレコードを開始
    navigator.device.capture.captureVideo(captureSuccess, captureError, {limit:2});

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Capture Video</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8" src="json2.js"></script>
        <script type="text/javascript" charset="utf-8">

        // レコードが完了した際に呼び出されるコールバック
        //
        function captureSuccess(mediaFiles) {
            var i, len;
            for (i = 0, len = mediaFiles.length; i < len; i += 1) {
                uploadFile(mediaFiles[i]);
            }	    
        }

        // 何らかのエラーが発生した際に呼び出されるコールバック
        // 
        function captureError(error) {
	        var msg = 'キャプチャ中にエラーが発生しました: ' + error.code;
            navigator.notification.alert(msg, null, 'Uh oh!');
        }

        function captureVideo() {
            // デバイスのビデオアプリを起動Launch device video recording application, 
            // ここでは二つのビデオのレコードを許可する。
            navigator.device.capture.captureVideo(captureSuccess, captureError, {limit: 2});
        }

        // サーバにファイルをアップロード
        function uploadFile(mediaFile) {
            var ft = new FileTransfer(),
                path = mediaFile.fullPath,
                name = mediaFile.name;

            ft.upload(path,
                "http://my.domain.com/upload.php",
                function(result) {
                    console.log('Upload success: ' + result.responseCode);
                    console.log(result.bytesSent + ' bytes sent');
                },
                function(error) {
                    console.log('Error uploading file ' + path + ': ' + error.code);
                },
                { fileName: name });   
        }

        </script>
        </head>
        <body>
            <button onclick="captureVideo();">Capture Video</button> <br>
        </body>
    </html>

BlackBerry WebWorks Quirks
--------------------------

- BlackBerry WebWorksに向けたPhoneGapはRIMによって提供されている __Video Recorder__ アプリを起動します。もしこのアプリケーションがデバイスにインストールされていない場合、 `CAPTURE_NOT_SUPPORTED` エラーコードを保持したCaptureError コールバックが呼び出されます。


