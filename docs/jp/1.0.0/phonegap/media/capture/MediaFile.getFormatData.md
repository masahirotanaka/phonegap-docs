MediaFile.getFormatData
=======================

> メディアのキャプチャファイルのフォーマットに関する情報を取得します。

    mediaFile.getFormatData( 
        MediaFileDataSuccessCB successCallback, 
        [MediaFileDataErrorCB errorCallback]
    );

概要
-----------

このメソッドはメディアファイルのフォーマットを取得する非同期関数です。取得に成功した場合は'MediaFileData'オブジェクトを引数に'MediaFileDataSuccessCB'が呼び出されます。また、取得に失敗した場合は、'MediaFileDataErrorCB'コールバック関数が呼び出されます。

サポートされているプラットフォーム
-------------------

- Android
- BlackBerry WebWorks (OS 5.0以上)
- iOS

BlackBerry WebWorksに関する注意点
--------------------------
BlackBerryではメディアファイルのフォーマットに関する情報を提供するAPIはありません。従って、'MediaFileData'オブジェクトは常にデフォルトの値を返します。詳しくはMediaFileDataを参照してください。


Androidに関する注意点
--------------
Androidにおけるメディアファイルのフォーマット情報の取得APIの数は限られています。従って、全てのMadiaFileDataオブジェクトがサポートされている訳ではありません。詳しくはMediaFileDataを参照してください。


iOSに関する注意点
----------
iOSにおけるメディアファイルのフォーマット情報の取得APIの数は限られています。従って、全てのMadiaFileDataオブジェクトがサポートされている訳ではありません。詳しくはMediaFileDataを参照してください。

