CaptureCB
=========

> Meidaオブジェクトに関するメソッドの成功時に呼び出されるコールバック関数

    function captureSuccess( MediaFile[] mediaFiles ) { ... };

概要
-----------

この関数はキャプチャが正常に完了した際に呼び出されるコールバック関数です。これはメディアファイルのキャプチャが完了した上で、ユーザがアプリを終了したかキャプチャ数が上限に達したことを意味します。

MediaFileオブジェクトがキャプチャされたメディアファイルの情報を保持しています。

使用例
-------------

    // 成功時のコールバック
    function captureSuccess(mediaFiles) {
        var i, path, len;
        for (i = 0, len = mediaFiles.length; i < len; i += 1) {
            path = mediaFiles[i].fullPath;
            // メディアファイルの処理を記述
        }
    };
