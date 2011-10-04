Contact
=======

 `Contact` オブジェクトは連絡先の詳細情報を保持しています。

プロパティ
----------

- __id:__ 連絡先を識別するためのID _(DOMString)_
- __displayName:__ 連絡先の名前 _(DOMString)_
- __name:__ 連絡先の名前に関する情報を保持するオブジェクト _(ContactName)_
- __nickname:__ 連絡先のニックネーム _(DOMString)_
- __phoneNumbers:__ 連絡先の電話番号情報を保持する配列 _(ContactField[])_
- __emails:__ 連絡先のEメールアドレス情報を保持する配列 _(ContactField[])_
- __addresses:__ 連絡先の住所情報を保持する配列 _(ContactAddresses[])_
- __ims:__ 連絡先のIMアドレス情報を保持する配列 _(ContactField[])_
- __organizations:__ 連絡先の組織情報を保持する配列 _(ContactOrganization[])_
- __birthday:__ 連絡先の誕生日 _(Date)_
- __note:__ 連絡先のメモ _(DOMString)_
- __photos:__ 連絡先の写真を保持する配列 _(ContactField[])_
- __categories:__  ユーザが定義したフィールドを保持する配列 _(ContactField[])_
- __urls:__  連絡先に関連したURLを保持する配列 _(ContactField[])_

メソッド
-------

- __clone__: このメソッドを呼び出した `Contact` オブジェクトのディープコピーを返します。ただし、idプロパティは'null'に設定されます。
- __remove__: デバイスのアドレス帳データベースから連絡先を削除します。
- __save__: デバイスのアドレス帳データベースに連絡先を保存・更新します。


詳細
-------

 `Contact` はユーザの連絡先を扱うオブジェクトです。`Contact` は生成、保存、削除をデバイスのアドレス帳データベースに対して行うことができます。 `contact.find` メソッドを用いて個々の連絡先をデータベースから取得し、処理することができます。


注意: 上記にある連絡先のフィールドは一部のプラットフォームではサポートされていない場合があります。詳しくは各プラットフォームごとの注意点を参照してください。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

Save 使用例
------------------

	function onSuccess(contact) {
		alert("保存に成功しました。");
	};

	function onError(contactError) {
		alert("Error = " + contactError.code);
	};

	// 新しい連絡先を作成
    var contact = navigator.contacts.create();
	contact.displayName = "Plumber";
	contact.nickname = "Plumber"; 		
	
	// フィールドを入力
	var name = new ContactName();
	name.givenName = "Jane";
	name.familyName = "Doe";
	contact.name = name;
	
	// デバイスに保存
	contact.save(onSuccess,onError);

Clone 使用例
-------------------

	// 連絡先をクローン
	var clone = contact.clone();
	clone.name.givenName = "John";
	console.log("Original contact name = " + contact.name.givenName);
	console.log("Cloned contact name = " + clone.name.givenName); 

Remove 使用例
--------------------

    function onSuccess() {
        alert("削除に成功しました。");
    };

    function onError(contactError) {
        alert("Error = " + contactError.code);
    };

	// 連絡先をデバイスから削除
	contact.remove(onSuccess,onError);

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
		    // 連絡先作成
		    var contact = navigator.contacts.create();
			contact.displayName = "Plumber";
			contact.nickname = "Plumber";
			var name = new ContactName();
			name.givenName = "Jane";
			name.familyName = "Doe";
			contact.name = name;

			// 保存
			contact.save(onSaveSuccess,onSaveError);
			
			//  コピー
			var clone = contact.clone();
			clone.name.givenName = "John";
			console.log("Original contact name = " + contact.name.givenName);
			console.log("Cloned contact name = " + clone.name.givenName); 
			
			// 削除
			contact.remove(onRemoveSuccess,onRemoveError);
        }
        
        // 保存成功時の処理: 連絡先を取得
        //
        function onSaveSuccess(contact) {
			alert("保存が成功しました。");
        }
    
        // 保存失敗時の処理: 保存が失敗したことをアラート
        //
        function onSaveError(contactError) {
			alert("Error = " + contactError.code);
        }
        
        // 削除成功時の処理: 連絡先を取得
        //
        function onRemoveSuccess(contacts) {
			alert("削除に成功しました。");
        }
    
        // 削除失敗時の処理: 削除に失敗したことをアラート
        //
        function onRemoveError(contactError) {
			alert("Error = " + contactError.code);
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

- __categories:__  Android 2.X ではこのプロパティはサポートされておらず、常に `null` を返します。

Android 1.X に関する注意点
------------------

- __name:__ Android 1.X ではこのプロパティはサポートされておらず、常に `null` を返します。
- __nickname:__ Android 1.X ではこのプロパティはサポートされておらず、常に `null` を返します。
- __birthday:__ Android 1.X ではこのプロパティはサポートされておらず、常に `null` を返します。
- __photos:__ Android 1.X ではこのプロパティはサポートされておらず、常に `null` を返します。
- __categories:__  Android 1.X ではこのプロパティはサポートされておらず、常に `null` を返します。
- __urls:__  Android 1.X ではこのプロパティはサポートされておらず、常に `null` を返します。


BlackBerry WebWorks (OS 5.0以上) に関する注意点
---------------------------------------------

- __id:__ 連絡先生成時にデバイスによって設定されます。
- __displayName:__ BlackBerryの __user1__ フィールドに保存されます。
- __nickname:__ BlackBerryではこのプロパティはサポートされておらず、常に `null` を返します。 
- __phoneNumbers:__ 部分的にサポートされています。電話番号はBlackBerryの __homePhone1__ と __homePhone2__ に保存されます( __type__ が'home'の場合)。また、 __type__  が'work'の場合は__workPhone1__ と __workPhone2__ へ, __type__ が'mobile'の場合は __mobilePhone__ へ, 'fax'の場合は __faxPhone__ へ, 'pager'の場合は __pagerPhone__ へ, __type__ がいずれの場合にも当てはまらない場合は __otherPhone__ へそれぞれ保存されます。
- __emails:__ 部分的にサポートされています。 3番目までのメールアドレスはBlackBerryの __email1__, __email2__, __email3__ へ、それぞれ保存されます。
- __addresses:__ 部分的にサポートされています。2番目までの住所はそれぞれBlackBerryの __homeAddress__ と __workAddress__ に保存されます。
- __ims:__ BlackBerryではこのプロパティはサポートされておらず、常に `null` を返します。 
- __organizations:__ 部分的にサポートされています。 最初の組織の __name__, __title__ フィールドはBlackBerryの __company__ と __title__ フィールドにそれぞれ保存されます。
- __photos:__ - サムネイルサイズの一つのイメージファイルのみサポートされています。連絡先の写真を設定する場合はbase64形式でエンコードされた画像文字列か画像の保存先URLを渡します。画像サイズはBlackBerryに保存される前に縮小されます。連絡先の画像はbase64形式でエンコードされた画像文字列で返されます。
- __categories:__  'Business', 'Personal' のみサポートされていません。
- __urls:__  部分的にサポートされています。1つ目のURLはBlackBerryの __webpage__ に保存されます。

iOSに関する注意点 
----------
- __displayName:__ このプロパティはiOSではサポートされていません。ただし、'ContactName'フィールドが空の場合はフルネーム、 __nickname__、もしくは "" が __displayName__ の代わりに返されます。
- __birthday:__ このフィールドにはJavaScriptのDateオブジェクトを格納してください。返り値もJavaScriptのDateオブジェクトとなります。
- __photos:__ Returned Photo is stored in the application's temporary directory and a File URL to photo is returned.  Contents of temporary folder is deleted when application exits. 
- __categories:__ このプロパティはiOSではサポートされておらず、常に'null'を返します。
