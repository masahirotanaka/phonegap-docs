camera.getPicture
=================

デフォルトのカメラアプリを利用しての写真撮影、フォトアルバムを呼び出して写真を選択をサポートするメソッドです。撮影した画像はbase64形式でエンコードされた文字列か、画像ファイルの保存先URIを返します。

    navigator.camera.getPicture( cameraSuccess, cameraError, [ cameraOptions ] );

概要
-----------

 `camera.getPicture` メソッドはデバイスに標準で備え付けられているカメラアプリを実行します。(この際 Camera.sourceType = Camera.PictureSourceType.CAMERA  となっており、この設定はデフォルトとなります) 写真の撮影が完了するとカメラアプリは終了し、アプリケーションに戻ります。

もし、 `Camera.sourceType = Camera.PictureSourceType.PHOTOLIBRARY` または `Camera.sourceType = Camera.PictureSourceType.SAVEDPHOTOALBUM` が設定されている場合は、写真選択ダイアログが開き、端末に保存されている画像を選択することができます。

このメソッドの返り値は `cameraOptions` にて指定されている設定に従って、下記のどちらかの文字列が `cameraSuccess` コールバック関数に渡されます:

- base64形式でエンコードされた画像の文字列 (デフォルト)
- 画像ファイルの保存先URIを示す文字列

取得した画像をもとに次のような処理を実装することができます:

- <img>タグを使って撮った写真を表示させる。
- 写真データをローカルに保存する。(`LocalStorage`, [Lawnchair](http://brianleroux.github.com/lawnchair/), etc)
- 撮った写真をリモートサーバに送信する。

注意: iPhone4やBlackBerry Touch 9800 などの最新デバイスで撮影されたイメージの画質は非常にきれいです。ただし、そのような画像データをbase64でエンコードするとメモリが足りなくなり、アプリがクラッシュする可能性があります。よって、FILE_URI を Camera.destinationType として使用することが推奨されます。

サポートされているプラットフォーム
-------------------

- Android
- Blackberry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

写真をとり、base64形式でエンコードされた画像の文字列を取得する:

    navigator.camera.getPicture(onSuccess, onFail, { quality: 50 }); 

    function onSuccess(imageData) {
        var image = document.getElementById('myImage');
        image.src = "data:image/jpeg;base64," + imageData;
    }

    function onFail(message) {
        alert('Failed because: ' + message);
    }

写真を撮影し、写真の保存先URIを取得します: 

    navigator.camera.getPicture(onSuccess, onFail, { quality: 50, 
        destinationType: Camera.DestinationType.FILE_URI }); 

    function onSuccess(imageURI) {
        var image = document.getElementById('myImage');
        image.src = imageURI;
    }

    function onFail(message) {
        alert('Failed because: ' + message);
    }


詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Capture Photo</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        var pictureSource;   // 写真の保存先
        var destinationType; // 返り値のフォーマットを指定
        
        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready",onDeviceReady,false);
    
        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            pictureSource=navigator.camera.PictureSourceType;
            destinationType=navigator.camera.DestinationType;
        }

        // 写真の取得に成功した場合に実行
        //
        function onPhotoDataSuccess(imageData) {
          // base64形式でエンコードされたイメージデータを表示する場合は下記のコメントを外す
          // console.log(imageData);
      
          // 取得したイメージを処理
          //
          var smallImage = document.getElementById('smallImage');
      
          // imgタグを表示
          //
          smallImage.style.display = 'block';
      
          // 撮った写真を表示
          // CSSで写真のサイズを変更する
          //
          smallImage.src = "data:image/jpeg;base64," + imageData;
        }

        // 写真の取得に成功した場合に実行
        //
        function onPhotoURISuccess(imageURI) {
          // イメージファイルのURIを表示させる場合は下記のコメントを外す 
          // console.log(imageURI);
      
          // 取得したイメージを処理
          //
          var largeImage = document.getElementById('largeImage');
      
          // imgタグを表示
          //
          largeImage.style.display = 'block';
      
          // 撮った写真を表示
          // CSSで写真のサイズを変更する
          //
          largeImage.src = imageURI;
        }

        // 下記のボタンにイベント登録
        //
        function capturePhoto() {
          // 写真を撮り、返り値としてイメージをbase64形式でエンコードした文字列を指定する
          navigator.camera.getPicture(onPhotoDataSuccess, onFail, { quality: 50 });
        }

        // 下記のボタンにイベント登録
        //
        function capturePhotoEdit() {
          // 写真を編集可能な状態で撮り、返り値としてイメージをbase64形式でエンコードした文字列を指定する 
          navigator.camera.getPicture(onPhotoDataSuccess, onFail, { quality: 20, allowEdit: true }); 
        }
    
        // 下記のボタンにイベント登録
        //
        function getPhoto(source) {
          // 写真を撮り、返り値としてイメージの保存先であるURIを指定するRetrieve image file location from specified source
          navigator.camera.getPicture(onPhotoURISuccess, onFail, { quality: 50, 
            destinationType: destinationType.FILE_URI,
            sourceType: source });
        }

        // 写真の取得に失敗した時に呼びだされる
        // 'message'には失敗理由が格納されている
        // 
        function onFail(message) {
          alert(message);
        }

        </script>
      </head>
      <body>
        <button onclick="capturePhoto();">Capture Photo</button> <br>
        <button onclick="capturePhotoEdit();">Capture Editable Photo</button> <br>
        <button onclick="getPhoto(pictureSource.PHOTOLIBRARY);">From Photo Library</button><br>
        <button onclick="getPhoto(pictureSource.SAVEDPHOTOALBUM);">From Photo Album</button><br>
        <img style="display:none;width:60px;height:60px;" id="smallImage" src="" />
        <img style="display:none;" id="largeImage" src="" />
      </body>
    </html>
