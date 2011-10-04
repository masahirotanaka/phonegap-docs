contacts.create
===============

新たな `Contact` オブジェクトを返します。

    var contact = navigator.contacts.create(properties);

概要
-----------

 `contacts.create` は `Contact` 新たにオブジェクトを作成する同期関数です。
このメソッドで生成された `Contact` オブジェクトはデバイスのデータベースには保存されません。生成した `Contact` オブジェクトを保存するためには `Contact.save` メソッドを使用します。


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

    var myContact = navigator.contacts.create({"displayName": "Test User"});

詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
			var myContact = navigator.contacts.create({"displayName": "Test User"});
			myContact.gender = "male";
			console.log( myContact.displayName + "の性別は" + myContact.gender + "です。" );
        }
    

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Create Contact</p>
      </body>
    </html>
