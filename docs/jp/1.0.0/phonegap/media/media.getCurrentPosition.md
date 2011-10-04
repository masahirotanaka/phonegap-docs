media.getCurrentPosition
========================

現在の再生位置を返します。

    media.getCurrentPosition(mediaSuccess, [mediaError]);

パラメータ
----------

- __mediaSuccess__: 現在の再生位置を引数に呼び出される成功時のコールバック関数
- __mediaError__: (Optional) 失敗時のコールバック関数

概要
-----------

Function `media.getCurrentPosition` is an asynchronous function that returns the current position of the underlying audio file of a Media object. Also updates the ___position__ parameter within the Media object. 
 `media.getCurrentPosition` はオーディオファイルの現在の再生位置を返す非同期関数です。 Mediaオブジェクトの __position__ パラメータの更新も行います。

サポートされているプラットフォーム
-------------------

- Android
- iOS
    
使用例
-------------

        // Mediaオブジェクトを生成
        //
        var my_media = new Media(src, onSuccess, onError);

        // 毎秒再生位置を更新
        var mediaTimer = setInterval(function() {
            // 再生位置を取得
            my_media.getCurrentPosition(
                // 成功時のコールバック
                function(position) {
                    if (position > -1) {
                        console.log((position) + " sec");
                    }
                },
                // 失敗時のコールバック
                function(e) {
                    console.log("Error getting pos=" + e);
                }
            );
        }, 1000);


詳細な使用例
------------

        <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
                      "http://www.w3.org/TR/html4/strict.dtd">
        <html>
          <head>
            <title>Media Example</title>
        
            <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
            <script type="text/javascript" charset="utf-8">
        
            // PhoneGapのロードを待機
            //
            document.addEventListener("deviceready", onDeviceReady, false);
        
            // PhoneGapのロードが完了
            //
            function onDeviceReady() {
                playAudio("http://audio.ibeat.org/content/p1rj1s/p1rj1s_-_rockGuitar.mp3");
            }
        
            var my_media = null;
            var mediaTimer = null;
        
            function playAudio(src) {
                // srcからMediaオブジェクトを生成 Create Media object from src
                my_media = new Media(src, onSuccess, onError);
        
                // オーディオを再生
                my_media.play();
        
                // 毎秒'my_media'の再生位置を更新
                if (mediaTimer == null) {
                    mediaTimer = setInterval(function() {
                        // 'my_media'の再生位置を取得
                        my_media.getCurrentPosition(
                            // 成功時のコールバック
                            function(position) {
                                if (position > -1) {
                                    setAudioPosition((position) + " sec");
                                }
                            },
                            // 失敗時のコールバック
                            function(e) {
                                console.log("Error getting pos=" + e);
                                setAudioPosition("Error: " + e);
                            }
                        );
                    }, 1000);
                }
            }
        
            // 録音を一時停止
            // 
            function pauseAudio() {
                if (my_media) {
                    my_media.pause();
                }
            }
        
            // 録音を停止
            // 
            function stopAudio() {
                if (my_media) {
                    my_media.stop();
                }
                clearInterval(mediaTimer);
                mediaTimer = null;
            }
        
            // 成功時のコールバック
            //
            function onSuccess() {
                console.log("playAudio():Audio Success");
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
            <a href="#" class="btn large" onclick="playAudio('http://audio.ibeat.org/content/p1rj1s/p1rj1s_-_rockGuitar.mp3');">Play Audio</a>
            <a href="#" class="btn large" onclick="pauseAudio();">Pause Playing Audio</a>
            <a href="#" class="btn large" onclick="stopAudio();">Stop Playing Audio</a>
            <p id="audio_position"></p>
          </body>
        </html>
