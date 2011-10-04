ContactAddress
==============

 `Contact` オブジェクトの住所プロパティを保持しているオブジェクトです。

プロパティ
----------
- __pref:__ `ContactAddress` にユーザ任意の値を保持させる場合は `true` に設定します。 _(boolean)_
- __type:__ このフィールドのタイプを表す文字列 (例: '自宅'). _(DOMString)
- __formatted:__ 住所 _(DOMString)_
- __streetAddress:__ ストリートアドレス _(DOMString)_
- __locality:__ 市 _(DOMString)_
- __region:__ 州、または地域 _(DOMString)_
- __postalCode:__ 郵便番号(zip code) _(DOMString)_
- __country:__ 国名 _(DOMString)_

詳細
-------

 `ContactAddress` オブジェクトは連絡先の住所情報を保持するオブジェクトです。 `Contact` オブジェクトは `ContactAddress[]` 配列に複数の住所を保存しておくことができます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

	// 全ての連絡先の住所情報を表示
    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			for (var j=0; j<contacts[i].addresses.length; j++) {
				alert("Pref: " + contacts[i].addresses[j].pref + "\n" +
						"Type: " + contacts[i].addresses[j].type + "\n" +
						"Formatted: " + contacts[i].addresses[j].formatted + "\n" + 
						"Street Address: "  + contacts[i].addresses[j].streetAddress + "\n" + 
						"Locality: "  + contacts[i].addresses[j].locality + "\n" + 
						"Region: "  + contacts[i].addresses[j].region + "\n" + 
						"Postal Code: "  + contacts[i].addresses[j].postalCode + "\n" + 
						"Country: "  + contacts[i].addresses[j].country);
			}
		}
    };

    function onError(contactError) {
        alert('エラーが発生しました。');
    };

    // 全ての連絡先を検索
    var options = new ContactFindOptions();
	options.filter=""; 
	var filter = ["displayName","addresses"];
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
		    // find all contacts
		    var options = new ContactFindOptions();
			options.filter=""; 
			var filter = ["displayName","addresses"];
		    navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // 成功時の処理: 連絡先の情報を取得
        //
		function onSuccess(contacts) {
			// display the address information for all contacts
			for (var i=0; i<contacts.length; i++) {
				for (var j=0; j<contacts[i].addresses.length; j++) {
					alert("Pref: " + contacts[i].addresses[j].pref + "\n" +
							"Type: " + contacts[i].addresses[j].type + "\n" +
							"Formatted: " + contacts[i].addresses[j].formatted + "\n" + 
							"Street Address: "  + contacts[i].addresses[j].streetAddress + "\n" + 
							"Locality: "  + contacts[i].addresses[j].locality + "\n" + 
							"Region: "  + contacts[i].addresses[j].region + "\n" + 
							"Postal Code: "  + contacts[i].addresses[j].postalCode + "\n" + 
							"Country: "  + contacts[i].addresses[j].country);
				}
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

Android 2.Xに関する注意点
------------------

- __pref:__ このプロパティはAndroid 2.xではサポートされておらず、常に `false` を返します。

Android 1.Xに関する注意点
------------------

- __pref:__ このプロパティはAndroid 1.xではサポートされておらず、常に `false` を返します。
- __type:__ このプロパティはAndroid 1.xではサポートされておらず、常に `null` を返します。
- __streetAddress:__ このプロパティはAndroid 1.xではサポートされておらず、常に `null` を返します。
- __locality:__ このプロパティはAndroid 1.xではサポートされておらず、常に `null` を返します。
- __region:__ このプロパティはAndroid 1.xではサポートされておらず、常に `null` を返します。
- __postalCode:__ このプロパティはAndroid 1.xではサポートされておらず、常に `null` を返します。
- __country:__ このプロパティはAndroid 1.xではサポートされておらず、常に `null` を返します。

BlackBerry WebWorks (OS 5.0以上) に関する注意点
--------------------------------------------
- __pref:__ このプロパティはBlackBerryではサポートされておらず、常に `false` を返します。
- __type:__ このプロパティは部分的にサポートされております。'Work'もしくは'Home'タイプのみ保存することが可能です。
- __formatted:__ このプロパティは部分的にサポートされております。 BlackBerryの住所に関するフィールドの連結を返します。
- __streetAddress:__ このプロパティはサポートされています。BlackBerryの __address1__ と __address2__ の連結を返します。
- __locality:__ このプロパティはサポートされています。BlackBerryの __city__ に保存されます。
- __region:__ このプロパティはサポートされています。  BlackBerryの __stateProvince__ に保存されます。
- __postalCode:__ このプロパティはサポートされています。BlackBerryの __zipPostal__ に保存されます。
- __country:__ このプロパティはサポートされています。

iOSに関する注意点
----------
- __pref:__ このプロパティはiOSではサポートされておらず、常に `false` を返します。
- __formatted:__ 現在はサポートされていません。
