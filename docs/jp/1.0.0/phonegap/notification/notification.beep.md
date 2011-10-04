notification.beep
=================

ビープサウンドを流します。

    navigator.notification.beep(times);

- __times:__ ビープを鳴らす回数 (`Number`)

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0以上)
- iPhone

使用例
-------------

    // ビープを二回鳴らす
    navigator.notification.beep(2);

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

        function showAlert() {
		    navigator.notification.alert(
		        'You are the winner!',  // メッセージ
		        'Game Over',            // タイトル
		        'Done'                  // ボトムネーム
		    );
        }

        // ビープを三回鳴らす
        //
        function playBeep() {
            navigator.notification.beep(3);
        }

        // 2秒間バイブレーションを作動する
        //
        function vibrate() {
            navigator.notification.vibrate(2000);
        }

        </script>
      </head>
      <body>
        <p><a href="#" onclick="showAlert(); return false;">Show Alert</a></p>
        <p><a href="#" onclick="playBeep(); return false;">Play Beep</a></p>
        <p><a href="#" onclick="vibrate(); return false;">Vibrate</a></p>
      </body>
    </html>

Androidに関する注意点
--------------

- Androidは"Settings/Sound & Display"パネルで指定されている、デフォルトの"Notification ringtone"を流します。

iPhoneに関する注意点
-------------

- __times__ パラメータを無視します。
- iPhoneにはビープに関するAPIは存在しません。
  - PhoneGapはビープをMedia APIを通じて実行します。
  - そのためユーザがビープとして使用するオーディオファイルを指定する必要があります。
  - そのファイルは30秒以下で、'www/'(root)ディレクトリ以下に置かれ、さらに'beep.wav'というファイル名を指定する必要があります。
