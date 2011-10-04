media.getDuration
=================

オーディオファイルの再生時間を返します。

    media.getDuration();


概要
-----------

 `media.getDuration` はオーディオファイルの再生時間を秒数で返す同期関数です。
もし再生時間が設定されていない場合は、'-1'を返します。

サポートされているプラットフォーム
-------------------

- Android
- iOS
    
使用例
-------------

        // Mediaオブジェクトを生成
        //
        var my_media = new Media(src, onSuccess, onError);

        // 再生時間を取得
        var counter = 0;
        var timerDur = setInterval(function() {
            counter = counter + 100;
            if (counter > 2000) {
                clearInterval(timerDur);
            }
            var dur = my_media.getDuration();
            if (dur > 0) {
                clearInterval(timerDur);
                document.getElementById('audio_duration').innerHTML = (dur) + " sec";
            }
       }, 100);


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
                // srcからMediaオブジェクトを生成
                my_media = new Media(src, onSuccess, onError);
        
                // オーディオを再生
                my_media.play();
        
                // 毎秒'my_media'の再生位置を更新
                if (mediaTimer == null) {
                    mediaTimer = setInterval(function() {
                        // 'my_media'の再生位置を取得
                        my_media.getCurrentPosition(
                            // 成功時のコールバック関数
                            function(position) {
                                if (position > -1) {
                                    setAudioPosition((position) + " sec");
                                }
                            },
                            // エラー時のコールバック関数
                            function(e) {
                                console.log("Error getting pos=" + e);
                                setAudioPosition("Error: " + e);
                            }
                        );
                    }, 1000);
                }
            }
        
            // オーディオを一時停止
            // 
            function pauseAudio() {
                if (my_media) {
                    my_media.pause();
                }
            }
        
            // オーディオを停止
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
