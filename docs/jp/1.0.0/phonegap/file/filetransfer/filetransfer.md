FileTransfer
==========

 `FileTransfer` オブジェクトはサーバにファイルをアップロードを可能にします。

プロパティ
----------

N/A

メソッド
-------

- __upload__: ファイルをサーバに送ります。

詳細
-------

`FileTransfer` オブジェクトはHTTPマルチポートPOSTリクエストを通じてファイルをリモートサーバにアップロードする手段を提供します。
プロトコルはHTTPとHTTPSの両方がサポートされています。 `FileUploadOptions` オブジェクトを `upload` メソッドに渡すことで、アップロードに関するオプションを指定することができます。
アップロードに成功した際には、 `FileUploadResult` オブジェクトを引数に成功時のコールバック関数が呼び出されます。エラー時には `FileTransferError` オブジェクトを引数に失敗時のコールバック関数が呼び出されます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
------------------------------
	
	// !! 変数'fileURI'がデバイスに保存されているテキストファイルのURIを保持していると仮定します。
	
  	var win = function(r) {
        console.log("Code = " + r.responseCode);
        console.log("Response = " + r.response);
        console.log("Sent = " + r.bytesSent);
	}
	
    var fail = function(error) {
        alert("エラーが発生しました: Code = " = error.code);
    }
	
	var options = new FileUploadOptions();
	options.fileKey="file";
	options.fileName=fileURI.substr(fileURI.lastIndexOf('/')+1);
	options.mimeType="text/plain";

    var params = new Object();
	params.value1 = "test";
	params.value2 = "param";
		
	options.params = params;
	
	var ft = new FileTransfer();
    ft.upload(fileURI, "http://some.server.com/upload.php", win, fail, options);
    
詳細な使用例
------------

    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
    <html>
    <head>
        <title>File Transfer Example</title>
    
        <script type="text/javascript" charset="utf-8" src="phonegap.0.9.4.min.js"></script>
        <script type="text/javascript" charset="utf-8">
            
            // PhoneGapのロードを待機
            //
            document.addEventListener("deviceready", onDeviceReady, false);
            
            // PhoneGapのロードが完了
            //
            function onDeviceReady() {
                
                // 指定されたソースから画像ファイルの保存先を取得Retrieve image file location from specified source
                navigator.camera.getPicture(uploadPhoto,
                                            function(message) { alert('画像の取得に失敗しました'); },
                                            { quality: 50, 
                                            destinationType: navigator.camera.DestinationType.FILE_URI,
                                            sourceType: navigator.camera.PictureSourceType.PHOTOLIBRARY }
                                            );
                
            }
            
            function uploadPhoto(imageURI) {
                var options = new FileUploadOptions();
                options.fileKey="file";
                options.fileName=imageURI.substr(imageURI.lastIndexOf('/')+1);
                options.mimeType="image/jpeg";
                
                var params = new Object();
                params.value1 = "test";
                params.value2 = "param";
                
                options.params = params;
                
                var ft = new FileTransfer();
                ft.upload(imageURI, "http://some.server.com/upload.php", win, fail, options);
            }
            
            function win(r) {
                console.log("Code = " + r.responseCode);
                console.log("Response = " + r.response);
                console.log("Sent = " + r.bytesSent);
            }
            
            function fail(error) {
                alert("An error has occurred: Code = " = error.code);
            }
            
            </script>
    </head>
    <body>
        <h1>Example</h1>
        <p>Upload File</p>
    </body>
    </html>

