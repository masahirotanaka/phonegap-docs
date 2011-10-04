cameraSuccess
=============

画像の取得に成功した際に呼び出されるコールバック関数です。撮影した写真のデータが引数に渡されます。

    function(imageData) {
        // 画像の処理を記述
    }

パラメータ
----------

- __imageData:__ Base64でエンコードされたイメージデータ、またはイメージファイルのURIが `cameraOptions` の設定に従って渡されます。 (`String`)

使用例
-------

    // イメージを表示
    //
    function cameraCallback(imageData) {
        var image = document.getElementById('myImage');
        image.src = "data:image/jpeg;base64," + imageData;
    }
