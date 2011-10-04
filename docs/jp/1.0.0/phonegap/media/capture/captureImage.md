capture.captureImage
====================

> カメラアプリを起動し、キャプチャした画像の情報を返します。

    navigator.device.capture.captureImage( 
	    CaptureCB captureSuccess, CaptureErrorCB captureError, [CaptureImageOptions options]
	);

概要
-----------

このメソッドはデバイスのデフォルトのカメラアプリを使って、画像キャプチャを非同期的に開始します。一回のセッションで複数のキャプチャを行うことができます。

キャプチャ処理はユーザがキャプチャをキャンセルするか、 __limit__ パラメータで指定されるキャプチャの最大件数に達した場合に終了します。もし、 __limit__ に値が指定されていない場合はデフォルトとして'1'が使われます。よってこの場合、ユーザが一つの録音を終了した時点でキャプチャは終了します。

キャプチャ操作が成功し正常に終了した際には、'CaptureCB'コールバックがキャプチャされた画像の情報を保持する'MediaFile'オブジェクトを引数に呼び出されます。
もしキャプチャが完了する前にユーザが処理をキャンセルした場合、`CaptureError.CAPTURE_NO_MEDIA_FILES`を保持する'CaptureError'オブジェクトを引数に'CaptureErrroCB'コールバック関数が呼び出されます。


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
            // メディアファイルの処理を記述
        }
    };

    // 失敗時のコールバック
    var captureError = function(error) {
        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
    };

    // 画像のキャプチャを開始
    navigator.device.capture.captureImage(captureSuccess, captureError, {limit:2});

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Capture Image</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8" src="json2.js"></script>
        <script type="text/javascript" charset="utf-8">

        // キャプチャが完了した際に呼び出されるコールバック
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

        function captureImage() {
            // デバイスのカメラアプリを起動
            // ここでは二つの画像のキャプチャを許可する。
            navigator.device.capture.captureImage(captureSuccess, captureError, {limit: 2});
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
            <button onclick="captureImage();">Capture Image</button> <br>
        </body>
    </html>


