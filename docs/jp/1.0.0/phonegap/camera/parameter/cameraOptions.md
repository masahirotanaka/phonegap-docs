cameraOptions
=============

カメラの設定をカスタマイズするためのオブジェクトです。


    { quality : 75, 
      destinationType : Camera.DestinationType.DATA_URL, 
      sourceType : Camera.PictureSourceType.CAMERA, 
      allowEdit : true,
      encodingType: Camera.EncodingType.JPEG,
      targetWidth: 100,
      targetHeight: 100 };

オプション
--------------

- __quality:__ 写真の画質。範囲: [0, 100]. (`Number`)

- __destinationType:__ 返り値のフォーマットを指定する。 navigator.camera.DestinationType で定義されています。(`Number`)
        
            Camera.DestinationType = {
                DATA_URL : 0,                // base64形式でエンコードされた画像の文字列を返す。
                FILE_URI : 1                 // 写真の保存先URIを返す。
            };

- __sourceType:__ 写真のソースを設定します。 nagivator.camera.PictureSourceType で定義されています。(`Number`)
     
        Camera.PictureSourceType = {
            PHOTOLIBRARY : 0,
            CAMERA : 1,
            SAVEDPHOTOALBUM : 2
        };

- __allowEdit:__ 写真選択の前に簡単な編集を可能にするオプションです。 (`Boolean`)
  
- __EncodingType:__ エンコードの形式を選択します。navigator.camera.EncodingType で定義されています。(`Number`)
        
            Camera.EncodingType = {
                JPEG : 0,               // JPEGでエンコードされたイメージを返します。
                PNG : 1                 // PNGでエンコードされたイメージを返します。
            };

- __targetWidth:__ 画像の横幅(ピクセル)。targetHeightと共に指定されなければ鳴らない。アスペクト比は保たれます。 (`Number`)
- __targetHeight:__ 画像の縦幅(ピクセル)。targetWidthと共に指定されなければ鳴らない。アスペクト比は保たれます。 (`Number`)
  
Androidに関する注意点
--------------

- Ignores the `allowEdit` parameter.
- Camera.PictureSourceType.PHOTOLIBRARY and Camera.PictureSourceType.SAVEDPHOTOALBUM both display the same photo album.
- Camera.EncodingType is not supported.

BlackBerryに関する注意点
-----------------

- `quality` は無視されます。
- `sourceType` は無視されます。
- `allowEdit` は無視されます。
- カメラを週リュするために、アプリケーションはキーインジェクションの許可を持たなければなりません。
- 解像度の高いカメラを持つデバイスで大きすぎる画像サイズを指定すると、エンコードに失敗する可能性があります。(例: Torch 9800)

Palm Quirks
-----------

- `quality` は無視されます。
- `sourceType` は無視されます。
- `allowEdit` は無視されます。

iPhoneに関する注意点
--------------

- いくつかのデバイスでクラッシュを防ぐために `quality` を50以下に設定してください。
- `destinationType.FILE_URI` が使われた場合、写真はアプリケーションのtemporaryディレクトリに保存されます。
- temporaryディレクトリの中身はアプリケーションが終了した際に削除されます。このディレクトリの中身は navigator.fileMgr APIを使って削除することもできます。
           
