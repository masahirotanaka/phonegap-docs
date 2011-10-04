media.startRecord
=================

オーディオファイルの録音を開始します。

    media.startRecord();


概要
-----------

 `media.startRecord` はオーディオファイルの録音を開始する同期関数です。

サポートされているプラットフォーム
-------------------

- Android
- iOS
    
使用例
-------------

    function recordAudio() {
        var src = "myrecording.mp3";
        var mediaRec = new Media(src,
            // 成功時のコールバック
            function() {
                console.log("recordAudio():Audio Success");
            },
            
            // 失敗時のコールバック
            function(err) {
                console.log("recordAudio():Audio Error: "+ err.code);
            });

        // 録音開始
        mediaRec.startRecord();
    }


詳細な使用例
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Device プロパティ Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGapのロードを待機
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // Record audio
        // 
        function recordAudio() {
            var src = "myrecording.mp3";
            var mediaRec = new Media(src, onSuccess, onError);

            // Record audio
            mediaRec.startRecord();

            // Stop recording after 10 sec
            var recTime = 0;
            var recInterval = setInterval(function() {
                recTime = recTime + 1;
                setAudioPosition(recTime + " sec");
                if (recTime >= 10) {
                    clearInterval(recInterval);
                    mediaRec.stopRecord();
                }
            }, 1000);
        }

        // PhoneGapのロードが完了
        //
        function onDeviceReady() {
            recordAudio();
        }
    
        // 成功時のコールバック
        //
        function onSuccess() {
            console.log("recordAudio():Audio Success");
        }
    
        // 失敗時のコールバック
        //
        function onError(error) {
            alert('code: '    + error.code    + '\n' + 
                  'message: ' + error.message + '\n');
        }

        // オーディオの再生位置をセット
        // 
        function setAudioPosition(position) {
            document.getElementById('audio_position').innerHTML = position;
        }

        </script>
      </head>
      <body>
        <p id="media">Recording audio...</p>
        <p id="audio_position"></p>
      </body>
    </html>


iOSに関する注意点
----------

- 録音の対象となるファイルは既にファイルシステム内に'.wav'形式で存在していなければなりません。また、FILE APIではそのようなファイルは作成できません。
