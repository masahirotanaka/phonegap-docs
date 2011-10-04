ContactField
============

電話番号、URL、Eメールアドレスなどのフィールドは `ContactField` オブジェクトに保存されます。

プロパティ
----------

- __type:__ フィールドのタイプを指定する文字列(例:電話番号) _(DOMString)_
- __value:__ フィールドタイプの値 _(DOMString)_
- __pref:__ `ContactField` にユーザ任意の値を持たせることを許可する場合は'true'設定 _(boolean)_

詳細
-------

 `ContactField` オブジェクトは連絡先のフィールドを汎用的な形でサポートする再利用可能なコンポーネントです。
全ての `ContactField` オブジェクトは __type__, __value__, __pref__プロパティを持ちます。一般的な `Contact` オブジェクトは電話番号やEメールアドレスといった複数のプロパティを `ContactField[]` 配列の中に持ちます。

 `ContactField` オブジェクトの __type__ プロパティはほとんどのケースであらかじめ一つに決まっている訳ではありません。例えば、'電話番号'は'自宅'、'職場'、'モバイル'、'iPhone'などといった __type__ を持つことができます。( __type__ に指定できる文字列は各デバイスによってサポートされている文字列に限定されます)
例外として、 `Contact` の __photos__ フィールドに関しては __value__ の値に従ってあらかじめ決まった文字列が __type__ プロパティに 格納されます。例えば、 __photos__ フィールドの __value__ プロパティが写真イメージのURLの場合、PhoneGapは __type__ プロパティに 'url' を格納します。また、 __value__ プロパティがbase64形式でエンコードされた画像の文字列の場合は、 __type__ プロパティには'base64'が格納されます。


サポートされているプラットフォーム
--------------------------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

	// 新しい連絡先を作成
	var contact = navigator.contacts.create();
	
	// 連絡先の電話番号を ContactField[] に格納
	var phoneNumbers = [3];
	phoneNumbers[0] = new ContactField('work', '212-555-1234', false);
	phoneNumbers[1] = new ContactField('mobile', '917-555-5432', true); // ユーザ任意の番号
	phoneNumbers[2] = new ContactField('home', '203-555-7890', false);
	contact.phoneNumbers = phoneNumbers;
	
	// 連絡先を保存
	contact.save();

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
			// 新しい連絡先を作成
			var contact = navigator.contacts.create();

			// 連絡先の電話番号を ContactField[] に格納
			var phoneNumbers = [3];
			phoneNumbers[0] = new ContactField('work', '212-555-1234', false);
			phoneNumbers[1] = new ContactField('mobile', '917-555-5432', true); // 任意の電話番号
			phoneNumbers[2] = new ContactField('home', '203-555-7890', false);
			contact.phoneNumbers = phoneNumbers;

			// 連絡先を保存
			contact.save();

			// 連絡先を検索し、ディスプレイ名と電話番号を返す
			var options = new ContactFindOptions();
			options.filter="";
			filter = ["displayName","phoneNumbers"];
			navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // 成功時の処理: 現在の連絡先情報を取得
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				// 電話番号を表示
				for (var j=0; j<contacts[i].phoneNumbers.length; j++) {
					alert("Type: " + contacts[i].phoneNumbers[j].type + "\n" + 
							"Value: "  + contacts[i].phoneNumbers[j].value + "\n" + 
							"Preferred: "  + contacts[i].phoneNumbers[j].pref);
				}
			}
		};
    
        // 失敗時の処理: 連絡先取得に失敗したことをアラート
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
--------------

- __pref:__ Androidではこのプロパティはサポートされておらず、常に'false'を返します。

BlackBerry WebWorks (OS 5.0以上) に関する注意点
--------------------------------------------

- __type:__ このプロパティは部分的にサポートされています。
- __value:__ このプロパティはサポートされています。
- __pref:__ BlackBerryではこのプロパティはサポートされておらず、常に'false'を返します。

iOSに関する注意点
-----------
- __pref:__ iOSではこのプロパティはサポートされておらず、常に'false'を返します。
