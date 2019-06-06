# ファームウエアの書き込み
### ファームウエアとはなにか
TONEでは、キー入力をPCに渡すために、QMKfirmwareを利用しています。  
QMKfirmwareは、先程とりつけたProMicroにこれから書き込まれ、キーの入力をPCで認識できる入力形式に変換して、PCに送る動作を行います。  
  
ProMicroは、Arduinoというプロジェクトで生産された、Leonardというシリーズの製品に対する愛称のようなものです。もし、あなたがキーボードを自作する場合、まだ暫くの間無視できないプロダクトであり続けるでしょう。  
  
### TONEの動作確認をする
まずは物理的にキーが動作しているか確認するためのファームウエアで、ハンダ付けがうまく行っているかを確認しましょう。  
  
テスト用のファームウエアはこちらに用意してあります。  
[TONE_test.hex](https://github.com/peraneko/TONE/blob/master/TONE_HEX/TONE_test.hex)  
TONE_test.hexをダウンロードして、わかりやすい場所に置いておきます。  
  
ファームウエアの書き込みについては、QMK Toolboxを利用します。
[QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases)  のダウンロード画面で、自分の使っているOSにあわせてダウンロードするファイルを選んでください。  
MAC OS/Windowsともに用意されています。  
  
QMK Toolboxを無事にダウンロードしたら、インストールして実行してください。  
このような画面が表示されます（Windows MACを利用している方は、適宜読み替えてください）  
![QMKToolbox実行画面](https://user-images.githubusercontent.com/5952961/59032589-a45a3c00-88a1-11e9-94c2-eec1b0bca2c6.png)  
この画面の右上、MicroContlorerのプルダウンがatmega32u4になっているか確認してください。  
問題がなければ、そのすぐ下にあるAuto-Flashのチェックボックスをクリックして、チェックを入れてください。  
  
左側のlocal fileを選択します。これは、書き込みたいファイルを指定するための動作です。
local fileの右側にあるOPENをクリックして、先程ダウンロードしておいた、TONE_test.hexを選択してください。  
  
選択したら、TONEのリセットスイッチを押します。
すると、自動的に書き込みが進んでいきます。すべて書き込まれると、PeranekoFactory:tone connectedと表示されます。
  
  
  

    
