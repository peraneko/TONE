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
  
QMK Toolboxを無事にダウンロードできたら、インストールして実行してください。  
このような画面が表示されます（Windows版 MACを利用している方は、適宜読み替えてください）  
![QMKToolbox実行画面](https://user-images.githubusercontent.com/5952961/59032589-a45a3c00-88a1-11e9-94c2-eec1b0bca2c6.png)  
この画面の右上、MicroContlorerのプルダウンがatmega32u4になっているか確認してください。  
問題がなければ、そのすぐ下にあるAuto-Flashのチェックボックスをクリックして、チェックを入れてください。  
  
左側のlocal fileを選択します。これは、書き込みたいファイルを指定するための動作です。
local fileの右側にあるOPENをクリックして、先程ダウンロードしておいた、TONE_test.hexを選択してください。  
  
選択したら、TONEのリセットスイッチを押します。
すると、自動的に書き込みが進んでいきます。  
書き込みが終わるとavrdude.exe done.  Thank you.と表示されます。
  
TONE_test.hexのキーマップは下記の通りです。  
~~~C
const uint16_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
  [0] = LAYOUT( 
    KC_A,  KC_B,  KC_C, KC_B,\
    KC_E,  KC_F,  KC_G, KC_H,\
    KC_0, KC_1 \
  ),
};

void encoder_update_user(uint16_t index, bool clockwise) {
  if (clockwise) {
    tap_code(KC_0);
  } else {
    tap_code(KC_1);
  }
}
~~~

上段の４キーが左からABCD  
下段の４キーが左からEFGH  
ロータリーエンコーダ時計回りが0  
反時計回りが1です。    
  
|　|左１|左２|左３|左４|時計回り|反時計回り|  
|---|---|---|---|---|---|---|---|  
||A|B|C|D|0|1|  
||E|F|G|H|||  




すべてのキーとロータリーエンコーダが正常に動いていることを確認したら、マクロパッドとしてのキーマップを書き込みましょう。
このキーマップは、Adobe photoshop Lightroom Classicでデモンストレーションを行うように設計されています。

~~~C
const uint16_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
  [0] = LAYOUT( 
    LCTL(LSFT(KC_E)),  LSFT(KC_TAB),   KC_TAB,         KC_0,\
    KC_LSFT,        LCTL(KC_LEFT),  LCTL(KC_RIGHT), LCTL(KC_Z),\
    KC_UP,          KC_DOWN\
  ),
};

void encoder_update_user(uint16_t index, bool clockwise) {
  if (clockwise) {
    tap_code(KC_UP);
  } else {
    tap_code(KC_DOWN);
  }
}
~~~
[TONE_ALR.hex](https://github.com/peraneko/TONE/blob/master/TONE_HEX/TONE_ALR.hex)  
TONE_ALR.hexをダウンロードして、わかりやすい場所に置き、先程の手順でProMicroに書き込んでみましょう。
  
上段の４キーが左からCtrl+SHIFTT+E（書き出し）　SHIFT+TAB　TAB　0    
下段の４キーが左からSHIFT　CTRL+←（前の画像）　CTRL＋→（次の画像） CTRL+Z  
ロータリーエンコーダ時計回りが↑
反時計回りが↓です。
  
