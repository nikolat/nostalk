# Resized Png Mini

[GitHub repository](https://github.com/tukinami/saori-resized-png-mini)

## これは何?

デスクトップマスコット、「伺か」で使用できるSAORIの一種です。

拙作[Resized Png](https://github.com/tukinami/saori-resized-png)
の機能限定・軽量版になります。

機能としては、指定した画像ファイルを拡大または縮小し、pngとして出力します。

`Resized Png`からの変更点として、読み込める画像形式が限定されています。

「伺か」「SAORI」等の用語については詳しく説明いたしませんのでご了承下さい。

## 使い方

SAORI自体の使い方は、使用するSHIORIなどによって異なりますので、ご自身でお調べ下さい。

ここではこのSAORIの使い方について説明いたします。

Argument0に、使用する機能名を指定して使用します。
指定できる機能は`GetImageType`と`GetImageInfo`と`ToResizedPng`です。

### `GetImageType`

+ Argument1: 判別するファイルのパス

+ Result: 画像形式を表す文字列

指定されたファイルの画像形式を返します。
画像でない、または対応していない画像は`UNKNOWN`が返ります。

対応している形式は以下(色深度などによっては、対応していない場合があります):

+ `BMP`
+ `GIF`
+ `JPEG`
+ `PNG`
+ `WEBP`

### `GetImageInfo`

+ Argument1: 情報を取得するファイルのパス

+ Result: エラーコードの数値(下記参照)
+ Value0: 画像の幅
+ Value1: 画像の高さ

入力された画像の幅と高さを出力します。
何か問題があった場合は、Resultに`0`以外が入ります。

### `ToResizedPng`

+ Argument1: 入力するファイルのパス
+ Argument2: 出力するファイルのパス
+ Argument3: 出力する画像の横幅の数値
+ Argument4: 出力する画像の縦幅の数値

+ Result: エラーコードの数値(下記参照)

入力された画像を拡大または縮小して、pngとして出力します。
何か問題があった場合は、Resultに`0`以外が入ります。

横幅と縦幅は、負の数を指定すると、もう片方の拡大縮小率に基づいて自動で値が決まります
(両方負の数にすると、何もせずに終了します)。
また、`0`を指定すると入力された画像の値を使用します。

### `GetImageInfo`と`ToResizedPng`のエラーコード

0. 正常終了
1. 対応していない形式だった
2. ファイルが見つからなかった
3. 入出力に問題があった
4. 画像のデコードに問題があった
5. 画像のエンコードに問題があった
6. 画像のパラメータに問題があった
7. 画像の大きさが限界値を越えていた
8. 画像サイズが小さすぎた

## 使用ライブラリ

いずれも敬称略。ありがとうございます。

+ [winapi\_rs](https://github.com/retep998/winapi-rs) / Peter Atashian
+ [png](https://github.com/image-rs/image-png) / The image-rs Developers
+ [gif](https://github.com/image-rs/image-gif) / The image-rs Developers
+ [jpeg-decoder](https://github.com/image-rs/jpeg-decoder) / The image-rs Developers
+ [tinybmp](https://github.com/embedded-graphics/tinybmp) / James Waples, Ralf Fuest
+ [embedded-graphics](https://github.com/embedded-graphics/embedded-graphics) / James Waples, Ralf Fuest
+ [resize](https://github.com/PistonDevelopers/resize) / Kornel, Kagami Hiiragi
+ [rgb](https://github.com/kornelski/rust-rgb) / Kornel Lesiński
+ [image-webp](https://github.com/image-rs/image-webp) / Jonathan Behrens
+ (テスト実行時) [encoding\_rs](https://github.com/hsivonen/encoding_rs) / Henri Sivonen
+ (テスト実行時) [tempfile](https://github.com/Stebalien/tempfile) / Steven Allen, The Rust Project Developers, Ashley Mannix, Jason White

## ライセンス

MITにて配布いたします。

## 作成者

月波 清火 (tukinami seika)

[GitHub](https://github.com/tukinami)
