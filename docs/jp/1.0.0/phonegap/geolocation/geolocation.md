Geolocation
===========

> `geolocation` オブジェクトはGPSを扱うためのオブジェクトです。

 `geolocation` は緯度/軽度などの位置情報を扱うためのオブジェクトです。
多くの場合、位置情報はGPSから取得されます。その他にもIPアドレス, RFID, WiFi, Blutooth MACアドレス, GSM/CDMA cell IDなどから位置情報を取得する場合もあります。なお、このAPIによって取得した位置情報がデバイスの正確な位置を示している保証はありません。

このAPIは[W3C Geo location API Specification](http://dev.w3.org/geo/api/spec-source.html)に準拠しています。既にW3Cの仕様に準拠しているデバイスに関しては、そのデバイスの実装を用いて位置情報を取得します。その他のデバイスに関してはPhoneGapの実装に従って位置情報を取得します。


メソッド
-------

- geolocation.getCurrentPosition
- geolocation.watchPosition
- geolocation.clearWatch


引数
---------

- geolocationSuccess
- geolocationError
- geolocationOptions

オブジェクト (読み込み専用)
-------------------

- Position
- PositionError
- Coordinates
