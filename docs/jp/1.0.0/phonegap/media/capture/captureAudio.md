capture.captureAudio
====================

> オーディオの録音アプリを起動し、キャプチャしたオーディオクリップに関する情報を返します。

    navigator.device.capture.captureAudio( 
	    CaptureCB captureSuccess, CaptureErrorCB captureError,  [CaptureAudioOptions options]
	);

概要
-----------

このメソッドはデバイスのデフォルト録音アプリを使って、オーディオキャプチャを非同期的に開始します。一回のセッションで複数の音声キャプチャを行うことができます。

キャプチャ処理はユーザが録音をキャンセルするか、 __limit__ パラメータで指定される録音の最大件数に達した場合に終了します。もし、 __limit__ に値が指定されていない場合はデフォルトとして'1'が使われます。よってこの場合、ユーザが一つの録音を終了した時点でキャプチャは終了します。

キャプチャ操作が成功し正常に終了した際には、'CaptureCB'コールバックがキャプチャされたオーディオクリップの情報を保持する'MediaFile'オブジェクトを引数に呼び出されます。
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

    // エラー時のコールバック
    var captureError = function(error) {
        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
    };

    // オーディオのキャプチャを開始
    navigator.device.capture.captureAudio(captureSuccess, captureError, {limit:2});

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Capture Audio</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8" src="json2.js"></script>
        <script type="text/javascript" charset="utf-8">

        // キャプチャが完了した際に呼び出されるコールバック関数
        //
        function captureSuccess(mediaFiles) {
            var i, len;
            for (i = 0, len = mediaFiles.length; i < len; i += 1) {
                uploadFile(mediaFiles[i]);
            }	    
        }

        // 何らかのエラーが発生した際に呼び出されるコールバック関数
        // 
        function captureError(error) {
	        var msg = 'An error occurred during capture: ' + error.code;
            navigator.notification.alert(msg, null, 'Uh oh!');
        }

        // A button will call this function
        //
        function captureAudio() {
            // デバイスの録音アプリを起動する。
            // ここでは二つのオーディオクリップのキャプチャを許可する。
            navigator.device.capture.captureAudio(captureSuccess, captureError, {limit: 2});
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
            <button onclick="captureAudio();">Capture Audio</button> <br>
        </body>
    </html>

BlackBerry WebWorksに関する注意点
--------------------------

- BlackBerry WebWorksに向けたPhoneGapはRIMによって提供されている __Voice Notes Recorder__ アプリを起動します。もしこのアプリケーションがデバイスにインストールされていない場合、 `CAPTURE_NOT_SUPPORTED` エラーコードを保持したCaptureError コールバックが呼び出されます。

iOSに関する注意点
--------------------

- iOSではデフォルトで録音アプリが備わっていないため、シンプルな録音アプリがPhoneGapにより提供されます。
