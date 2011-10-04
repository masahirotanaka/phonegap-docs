notification.confirm
====================

カスタムの認証ダイアログボックスを表示します。

    navigator.notification.confirm(message, confirmCallback, [title], [buttonLabels])

- __message:__ ダイアログメッセージ (`String`)
- __confirmCallback:__ - ボタンのインデックス(例:1, 2, 3...)が押された際に呼び出されるコールバック関数 (`Number`)
- __title:__ ダイアログのタイトル (`String`) (Optional, デフォルト: "Confirm")
- __buttonLabels:__ コンマで分割されたボックスの下部に表示される文字列 (`String`) (Optional, デフォルト: "OK,Cancel")
    
概要
-----------

 `notification.confirm`はブラウザの `confirm` 関数よりもカスタマイズ姓に富んだネイティブのダイアログボックスを表示させます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

	// 認証の結果に処理を加える
	function onConfirm(button) {
		alert('You selected button ' + button);
	}

    // カスタム認証ダイアログを表示
    //
    function showConfirm() {
        navigator.notification.confirm(
	        'You are the winner!',  // メッセージ
			onConfirm,				// ボタンインデックスと共に呼ばれるコールバック
	        'Game Over',            // タイトル
	        'Restart,Exit'          // ボトムラベル
        );
    }
        
詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Notification Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {

        }
    
		// 認証の結果に処理を加える
		function onConfirm(button) {
			alert('You selected button ' + button);
		}

        // カスタムの認証ダイアログを表示
        //
        function showConfirm() {
            navigator.notification.confirm(
		        'You are the winner!',  // メッセージ
				onConfirm,				// ボタンインデックスと共に呼ばれるコールバック
		        'Game Over',            // タイトル
		        'Restart,Exit'          // ボタンラベル
            );
        }
    
        </script>
      </head>
      <body>
        <p><a href="#" onclick="showConfirm(); return false;">Show Confirm</a></p>
      </body>
    </html>
