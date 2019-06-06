# ファームウエアの書き込み
### ファームウエアとはなにか
TONEでは、キー入力をPCに渡すために、QMKfirmwareを利用しています。  
QMKfirmwareは、先程とりつけたProMicroにこれから書き込まれ、キーの入力をPCで認識できる入力形式に変換して、PCに送る動作を行います。  
  
ProMicroは、Arduinoというプロジェクトで生産された、Leonardというシリーズの製品に対する愛称のようなものです。もし、あなたがキーボードを自作する場合、まだ暫くの間無視できないプロダクトであり続けるでしょう。  
  
### TONEの動作確認をする
まずは物理的にキーが動作しているか確認するためのファームウエアで、ハンダ付けがうまく行っているかを確認しましょう。  
ファームウエアの書き込みについては、QMK Toolboxを利用します。
[QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases)  
QMK Toolboxのダウンロードは、自分の使っているOSにあわせて選んでください。  
MAC OS/Windowsともに用意されています。  
  
QMK Toolboxを無事にダウンロードしたら、インストールして実行してください。  
このような画面が表示されます（Windows MACを利用している方は、適宜読み替えてください）  
![QMKToolbox実行画面](https://user-images.githubusercontent.com/5952961/59030186-3d398900-889b-11e9-9e33-f862b5cb6893.png)