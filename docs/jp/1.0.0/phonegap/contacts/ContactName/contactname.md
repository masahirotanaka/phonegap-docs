ContactName
===========

 `ContactName` は `Contact` オブジェクトの名前に関するプロパティを保持するオブジェクトです。

プロパティ
----------

- __formatted:__ フルネーム _(DOMString)_
- __familyName:__ 姓 _(DOMString)_
- __givenName:__ 名 _(DOMString)_
- __middleName:__ ミドルネーム _(DOMString)_
- __honorificPrefix:__ 接頭敬称 (例: Mr., Dr., etc...) _(DOMString)_
- __honorificSuffix:__ 接尾敬称 (例: Esq.). _(DOMString)_

詳細
-------

 `ContactName` は連絡先の名前に関するプロパティを保持しています。

サポートされているプラットフォーム
--------------------------------------

- Android 2.X
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			alert("Formatted: " + contacts[i].name.formatted + "\n" + 
					"Family Name: "  + contacts[i].name.familyName + "\n" + 
					"Given Name: "  + contacts[i].name.givenName + "\n" + 
					"Middle Name: "  + contacts[i].name.middleName + "\n" + 
					"Suffix: "  + contacts[i].name.honorificSuffix + "\n" + 
					"Prefix: "  + contacts[i].name.honorificSuffix);
		}
    };

    function onError(contactError) {
        alert('エラーが発生しました。');
    };

    var options = new ContactFindOptions();
	options.filter="";
	filter = ["displayName","name"];
    navigator.contacts.find(filter, onSuccess, onError, options);

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
			var options = new ContactFindOptions();
			options.filter="";
			filter = ["displayName","name"];
			navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // 成功時の処理: 連絡先を取得
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				alert("Formatted: " + contacts[i].name.formatted + "\n" + 
						"Family Name: "  + contacts[i].name.familyName + "\n" + 
						"Given Name: "  + contacts[i].name.givenName + "\n" + 
						"Middle Name: "  + contacts[i].name.middleName + "\n" + 
						"Suffix: "  + contacts[i].name.honorificSuffix + "\n" + 
						"Prefix: "  + contacts[i].name.honorificPrefix);
			}
		};
    
        // 失敗時の処理: 連絡先の取得に失敗したことをアラート
        //
        function onError(contactError) {
            alert('エラーが発生しました。');
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Find Contacts</p>
      </body>
    </html>

Androidに関する注意点
------------------------
- __formatted:__ 部分的にサポートされています。

BlackBerry WebWorks (OS 5.0以上) に関する注意点
---------------------------------------------

- __formatted:__ 部分的にサポートされています。BlackBerryの __firstName__ と __lastName__ の結合を保持しています。
- __familyName:__ サポートされています。  BlackBerryの __lastName__ フィールドに保存されます。
- __givenName:__ サポートされています。  Stored in BlackBerry __firstName__ field.
- __middleName:__ このプロパティはBlackBerryではサポートされておらず、常に `null` を返します。
- __honorificPrefix:__ このプロパティはBlackBerryではサポートされておらず、常に `null` を返します。
- __honorificSuffix:__ このプロパティはBlackBerryではサポートされておらず、常に `null` を返します。

iOSに関する注意点
------------
- __formatted:__ 部分的にサポートされています。
