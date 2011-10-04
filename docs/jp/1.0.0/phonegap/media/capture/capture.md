Capture
=======

> 'capture'オブジェクトProvides access to the audio, image, and video capture capabilities of the device.

オブジェクト
-------

- Capture
- CaptureAudioOptions
- CaptureImageOptions
- CaptureVideoOptions
- CaptureCB
- CaptureErrorCB
- ConfigurationData
- MediaFile
- MediaFileData

メソッド
-------

- capture.captureAudio
- capture.captureImage
- capture.captureVideo
- MediaFile.getFormatData

Scope
-----

 __capture__ オブジェクトは __navigator.device__ オブジェクトにアサインされるため、グローバルスコープを持ちます。

    // The global capture object
    var capture = navigator.device.capture;

プロパティ
----------

- __supportedAudioModes:__ オーディオの録音フォーマット (ConfigurationData[])
- __supportedImageModes:__ 画像サイズとフォーマット (ConfigurationData[])
- __supportedVideoModes:__ ビデオの解像度とフォーマット (ConfigurationData[])

メソッド
-------

- capture.captureAudio: ネイティブの録音アプリを起動します。
- capture.captureImage: ネイティブの画像キャプチャアプリを起動します。
- capture.captureVideo: ネイティブのビデオキャプチャアプリを起動します。


サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS
