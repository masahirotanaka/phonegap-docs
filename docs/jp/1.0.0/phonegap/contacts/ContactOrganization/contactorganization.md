ContactOrganization
===================

 `Contact` オブジェクトの組織に関するプロパティを保持しています。

プロパティ
----------
- __pref:__ `ContactOrganization` がユーザ任意の値を保持することを許可する場合は `true` に設定 _(boolean)_
- __type:__ フィールドのタイプを指定する文字列 _(DOMString)
- __name:__ 組織名 _(DOMString)_
- __department:__ 部署 _(DOMString)_
- __title:__ 肩書き _(DOMString)_

詳細
-------

 `ContactOrganization` は連絡先の組織に関する情報を保持しています。 `Contact` オブジェクトは複数の `ContactOrganization` オブジェクトを配列として保持しています。


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			for (var j=0; j<contacts[i].organizations.length; j++) {
				alert("Pref: " + contacts[i].organizations[j].pref + "\n" +
						"Type: " + contacts[i].organizations[j].type + "\n" +
						"Name: " + contacts[i].organizations[j].name + "\n" + 
						"Department: "  + contacts[i].organizations[j].department + "\n" + 
						"Title: "  + contacts[i].organizations[j].title);
			}
		}
    };

    function onError(contactError) {
        alert('エラーが発生しました。');
    };

    var options = new ContactFindOptions();
	options.filter="";
	filter = ["displayName","organizations"];
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
			filter = ["displayName","organizations"];
			navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // 成功時の処理: 連絡先を取得
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				for (var j=0; j<contacts[i].organizations.length; j++) {
					alert("Pref: " + contacts[i].organizations[j].pref + "\n" +
							"Type: " + contacts[i].organizations[j].type + "\n" +
							"Name: " + contacts[i].organizations[j].name + "\n" + 
							"Department: "  + contacts[i].organizations[j].department + "\n" + 
							"Title: "  + contacts[i].organizations[j].title);
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
	

Android 2.X に関する注意点
------------------

- __pref:__ このプロパティはAndroid 2.x ではサポートされておらず、常に `false` を返します。

Android 1.X に関する注意点
------------------

- __pref:__ このプロパティはAndroid 1.x ではサポートされておらず、常に `false` を返します。
- __type:__ このプロパティはAndroid 1.x ではサポートされておらず、常に `null` を返します。
- __title:__ このプロパティはAndroid 1.x ではサポートされておらず、常に `null` を返します。 

BlackBerry WebWorks (OS 5.0以上) に関する注意点
--------------------------------------------
- __pref:__ このプロパティは Black Berry ではサポートされておらず、常に `false` を返します。
- __type:__ このプロパティは Black Berry ではサポートされておらず、常に `null` を返します。
- __name:__ このプロパティは部分的にサポートされています。最初の組織名はBlack Berryの __company__ フィールドに保存されます。
- __department:__ このプロパティは Black Berry ではサポートされておらず、常に `null` を返します。
- __title:__ このプロパティは部分的にサポートされています。最初の組織名はBlack Berryの __jobTitle__ フィールドに保存されます。

iOSに関する注意点
-----------
- __pref:__ このプロパティはiOSではサポートされておらず、常に `false` を返します。
- __type:__ このプロパティはiOSではサポートされておらず、常に `null` を返します。
- __name:__ このプロパティは部分的にサポートされています。最初の組織名はiOSの __kABPersonOrganizationProperty__ フィールドに保存されます。
- __department__: このプロパティは部分的にサポートされています。最初の部署名はiOSの __kABPersonDepartmentProperty__ フィールドに保存されます。
- __title__: このプロパティは部分的にサポートされています。最初の肩書きはiOSの __kABPersonjobTitleProperty__ フィールドに保存されます。


