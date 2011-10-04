ContactFindOptions
==================

 `ContactFindOptions` は `contacts.find` メソッドの結果にフィルターをかける場合に使用します。

プロパティ
----------

- __filter:__ 連絡先検索のフィルターに用いる文字列 _(DOMString)_ (Default: "")
- __multiple:__ `contact.find` メソッドが複数の連絡先を返すことを許可する場合は `true` を設定 _(Boolean)_ (Default: false)


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

使用例
-------------

	// 成功時のコールバック
    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			alert(contacts[i].displayName);
		}
    };

	// エラー時のコールバック
    function onError(contactError) {
        alert('エラーが発生しました。');
    };

	// サーチのフィルターを設定
    var options = new ContactFindOptions();
	options.filter="";			// 空の文字列は全ての連絡先を返却
	options.multiple=true;		// 複数の連絡先を返却
	filter = ["displayName"];	// 'contact.displayName' フィールドを返却
	
	// 連絡先を検索
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
			// サーチのフィルターを設定
		    var options = new ContactFindOptions();
			options.filter="";			// 空の文字列は全ての連絡先を返却
			options.multiple=true;		// 複数の連絡先を返却
			filter = ["displayName"];	// 'contact.displayName' フィールドを返却

			// find contacts
		    navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // 成功時の処理: 連絡先を取得
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				alert(contacts[i].displayName);
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

