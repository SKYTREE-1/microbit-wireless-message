# 無線通信：メッセージを送ろう

## このチュートリアルでやること  @unplugged

micro:bitには、ほかのmicro:bitと無線で情報をやりとりする機能があります。

ここでは、2台のmicro:bitを使って、

- 数字を送る
- 送った数字を受け取る

という無線通信の基本を体験してみましょう。

![文字列の表示](https://raw.githubusercontent.com/NBSTT/pxt-my-an/refs/heads/master/image/microbit-hello.gif)




## 1. 2台のmicro:bitを用意しよう  @unplugged

micro:bitを2台用意します。

ここでは、それぞれを「A」と「B」と呼ぶことにします。

- micro:bit A：送信する
- micro:bit B：受信する

ただし、AとBは固定ではありません。
どちらのmicro:bitからも送信できます。



## 2. 無線グループを設定しよう @unplugged

無線通信では、同じグループに設定したmicro:bitどうしで通信します。

2台とも、同じ無線グループに設定しましょう。

### ポイント

同じグループに設定することで、
同じグループのmicro:bitにメッセージを送ることができます。


## 2-1 無線グループの設定
メニューの ``||radio:無線||`` の ``||radio:無線グループを設定||``ブロックを ``||basic:最初だけ||``にいれて、番号をセットする。

```blocks
radio.setGroup(1)

```

## 3. Aボタンを押したら「1」を送ろう  @unplugged

まず、Aボタンを押したときに、
数字の `1` を無線で送るプログラムを作ります。



## 3-1 プログラム
メニューの ``||input:入力||`` の ``||input:Aボタンが押されたとき||``を配置して、そこに、``||radio:無線||`` グループの``||radio:無線で数値を送信||``ブロックをあてはめ、数を1にかえる。 

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(1)
})
```

## 4. 送られてきた数字を表示しよう  @unplugged
次に、もう一台の micro:bit で、数字を受け取ったら表示するプログラムを作ります。



## 4-1 プログラム

メニューの ``||radio:無線||`` の ``||radio:無線で受信したとき(recievedNumber)||``
を配置して``||basic:基本||``グループの``||basic:数を表示||`` を配置して、数のところに
``||radio:無線で受信したとき(recievedNumber)||``から、
``||variables:recievedNumber||`` の部分をひっぱってきてあてはめます。 


```blocks
radio.onReceivedNumber(function (receivedNumber) {
    basic.showNumber(receivedNumber)
})
```

## 2台のmicroに同じプログラムを書き込もう @unplugged

ここまでで、1つのプログラムを作りました。

このプログラムには、

```
* Aボタンを押したら 1 を送る
* 数字を受信したら、その数字を表示する
```

という2つの動作が入っています。
ここで、この同じプログラムを2台のmicro:bitに書き込んでみましょう。

2台とも同じプログラムで動くので、どちらのmicro:bit からでも数字を送ることができます。

実際に2台でメッセージを送り合ってみましょう。

### ポイント

無線通信では、同じグループに設定したmicro:bit に、同じプログラムを書き込んで使うことができます。

## ダウンロード

実際に２台のmicro:bitにダウンロードしてください。
パソコンにつながないmicro:bit は電池ボックスをつけて、電池で動くようにします。

## 5. Bボタンでも作ってみよう  @unplugged

今度は、Bボタンを押したら 2 を送るようにしてみよう。

```text
Aボタン → 1を送信
Bボタン → 2を送信
```

できたら、2台のmicro:bitを使って、
どちらから送っても数字が届くことを確認してください。

注意：プログラムを書き込むときは２台に書き込みましょう。

## 5-1 プログラム
メニューの ``||input:入力||`` の ``||input:Aボタンが押されたとき||``を配置して、AをBに変え、
そこに、``||radio:無線||`` グループの``||radio:無線で数値を送信||``ブロックをあてはめ、数を2にかえる。 



```blocks
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(2)
})

```
## 5-2 ダウンロード
できたら、ダウンロードして実行してみよう。

## 6. 少し改造しよう @unplugged

送る数字を、自分で変えてみよう。

例：
```text
Aボタン → 10
Bボタン → 20
```

できたら、2台のmicro:bitを使って、
変更した数字が、受信側の micro:bitに正しく表示されるか確認しましょう。

注意：プログラムを書き込むときは２台に書き込みましょう。

## 6-1 プログラム
送る数を自由に変えたら、ダウンロードして実行してみよう。

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(10)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(20)
})

```

## 7. Finish  @unplugged

これで、micro:bitから別のmicro:bitへ
無線で数字を送ることができました。
次は、この「数字を送る」仕組みを使って、
2人でゲームを作ってみましょう。

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    basic.showNumber(receivedNumber)
})
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(10)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(20)
})
radio.setGroup(1)
```

