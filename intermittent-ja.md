# 間欠歯車

[[fusion360-study-gears チュートリアルへ戻る]](https://github.com/osamutake/fusion360-study-gears/blob/main/README-ja.md#チュートリアル)

間欠歯車を作り動かしてみます。

<a href="assets/intermittent40.gif"><img src="assets/intermittent40.gif" width="500"></a>

このページで作成する間欠歯車は図のようなもので以下の特徴を持っています。

- 右の歯車が１周すると左の歯車が 1/4 回転する
- 左の歯車は歯数８の歯車が元になっている
  - 上半分は歯数８の歯車そのもの
  - 下半分については１枚おきに歯が削られている
- 右の歯車は歯数２０の歯車が元になっている
  - 歯先円は小歯車と干渉しないよう半径が小さく取られている
  - 上半分は２枚だけ歯を残して残りは削られている
  - 下半分は２枚の歯の間のみ歯溝が切られている
- 右の歯車の２枚の歯により動力が伝えられる
- 歯が噛み合っていない間は右の歯車の下半分の歯先円と左の小歯車の下半分の１枚おきに残された歯とが触れ合うことにより、小歯車は回転しないよう固定される

以下に設計方法と Fusion360 によるシミュレーション方法を紹介する。

## 歯車の生成

歯数 8 と歯数 20 の歯車をモジュール 4 厚さ 10 mm として生成します。

<a href="assets/intermittent1.jpg"><img src="assets/intermittent1.jpg" width="300"></a>
<a href="assets/intermittent2.jpg"><img src="assets/intermittent2.jpg" width="300"></a>

## 噛み合い位置へ移動

大歯車のコンポーネントを x 軸方向へ $4\,\mathrm{mm}\times(8+20)/2$ だけ移動

小歯車のボディを回転軸周りに $360\,\mathrm{deg}/8/2$ だけ回転

<a href="assets/intermittent3.jpg"><img src="assets/intermittent3.jpg" width="300"></a>
<a href="assets/intermittent4.jpg"><img src="assets/intermittent4.jpg" width="300"></a>

## 小歯車の下半分の歯を１枚おきに除去する

xy 平面上に新しいスケッチを作成する
- その際、歯車コンポーネントの位置をキャプチャしておく

<a href="assets/intermittent5.jpg"><img src="assets/intermittent5.jpg" width="300"></a>
<a href="assets/intermittent6.jpg"><img src="assets/intermittent6.jpg" width="300"></a>

小歯車をスケッチ上に射影する
- 歯車の上で右クリック
- スケッチを選択
- 射影を選択
- フィルターをボディにして歯車を選択しＯＫ

<a href="assets/intermittent7.jpg"><img src="assets/intermittent7.jpg" width="300"></a>
<a href="assets/intermittent8.jpg"><img src="assets/intermittent8.jpg" width="300"></a>
<a href="assets/intermittent9.jpg"><img src="assets/intermittent9.jpg" width="300"></a>

歯元円を描く
- 歯車の中心(原点)から歯元の点までを半径とした円を描く

<a href="assets/intermittent10.jpg"><img src="assets/intermittent10.jpg" width="300"></a>

図の４枚の歯を選び、押し出しにより歯を除去する

<a href="assets/intermittent11.jpg"><img src="assets/intermittent11.jpg" width="300"></a>
<a href="assets/intermittent12.jpg"><img src="assets/intermittent12.jpg" width="300"></a>

## 大歯車の歯先を縮める

大歯車の基準円を元に新たにスケッチを作成

<a href="assets/intermittent13.jpg"><img src="assets/intermittent13.jpg" width="300"></a>

小歯車の歯形を射影し 0.1 mm オフセットした曲線を生成

<a href="assets/intermittent14.jpg"><img src="assets/intermittent14.jpg" width="300"></a>
<a href="assets/intermittent15.jpg"><img src="assets/intermittent15.jpg" width="300"></a>

大歯車の中心（スケッチの原点）から円を描く

上で生成したオフセット曲線に接触させる
- なぜか２つの間に接線制約を設定できないため目分量で接触させる

<a href="assets/intermittent16.jpg"><img src="assets/intermittent16.jpg" width="300"></a>
<a href="assets/intermittent17.jpg"><img src="assets/intermittent17.jpg" width="300"></a>

円を両側へ無限遠まで押し出して歯車との共通部分を残す

<a href="assets/intermittent18.jpg"><img src="assets/intermittent18.jpg" width="300"></a>

これで大歯車の歯先が切り取られました。

## 大歯車の下半分を作成する

大歯車の基準円を元に新たにスケッチを作成 (図は省略)

図のように歯先の２点を選択してスケッチに射影する

この２点を基準にして２つの半径と円弧を描く

得られたプロファイルを押し出すことで１つを除いて歯溝を埋める

<a href="assets/intermittent19.jpg"><img src="assets/intermittent19.jpg" width="300"></a>
<a href="assets/intermittent22.jpg"><img src="assets/intermittent22.jpg" width="300"></a>
<a href="assets/intermittent23.jpg"><img src="assets/intermittent23.jpg" width="300"></a>

次の作業のために視点を反対側に持って来る

<a href="assets/intermittent24.jpg"><img src="assets/intermittent24.jpg" width="300"></a>
<a href="assets/intermittent25.jpg"><img src="assets/intermittent25.jpg" width="300"></a>

## 大歯車の上半分を作成する

大歯車の基準円を元に新たにスケッチを作成

図のように x 軸から $360\,\mathrm{deg}/20$ だけ傾けて直線を描く

x 軸に対して鏡像を作成する

歯先円よりも大きく円弧を描く

<a href="assets/intermittent26.jpg"><img src="assets/intermittent26.jpg" width="300"></a>
<a href="assets/intermittent27.jpg"><img src="assets/intermittent27.jpg" width="300"></a>
<a href="assets/intermittent28.jpg"><img src="assets/intermittent28.jpg" width="300"></a>
<a href="assets/intermittent29.jpg"><img src="assets/intermittent29.jpg" width="300"></a>

歯底の点をスケッチ上に射影

その点を通り２つの半径と交わる円弧を描く

<a href="assets/intermittent30.jpg"><img src="assets/intermittent30.jpg" width="300"></a>
<a href="assets/intermittent31.jpg"><img src="assets/intermittent31.jpg" width="300"></a>

プロファイルを押し出し２枚を残して歯を除去する

<a href="assets/intermittent32.jpg"><img src="assets/intermittent32.jpg" width="300"></a>

## 歯車の回転軸を固定する

２つの歯車コンポーネントとルートコンポーネントを含む剛性グループを作成します
- ２つの歯車コンポーネントを選択して剛性グループの作成を選択
- 回転軸を含むがよいかと聞かれるので Yes を選択
- 子コンポーネントを含める、のチェックを解除
- ルートコンポーネントを追加で選択してＯＫ

<a href="assets/intermittent34.jpg"><img src="assets/intermittent34.jpg" width="260"></a>
<a href="assets/intermittent35.jpg"><img src="assets/intermittent35.jpg" width="240"></a>

<a href="assets/intermittent36.jpg"><img src="assets/intermittent36.jpg" width="200"></a>
<a href="assets/intermittent37.jpg"><img src="assets/intermittent37.jpg" width="200"></a>

## 歯車の間に接触セットを設定

アセンブルメニューから接触セットを有効化

新しい接触セットを作成

２つの歯車を選択してＯＫ

<a href="assets/intermittent38.jpg"><img src="assets/intermittent38.jpg" width="400"></a>

<a href="assets/intermittent39.jpg"><img src="assets/intermittent39.jpg" width="300"></a>


<a href="assets/intermittent33.jpg"><img src="assets/intermittent33.jpg" width="300"></a>

## 回転させてみる

本来これで良いはずなのですが、
接触セットによる解析がうまく行かずなかなかスムーズに回せないようです？

普通の歯車を回転させるのとほとんど変わらないように思えるのですが・・・

何とか動画にしたのがこちらです。

<a href="assets/intermittent40.gif"><img src="assets/intermittent40.gif" width="600"></a>

ここで作成した間欠歯車は小歯車の回転速度が不連続に変化するため
滑らかな動作は期待できないことが分かります。

これは同じく間欠動作をする [ゼネバ歯車](geneva-ja.md)
が速度ゼロから徐々に加速するのと大きく違なります。

ここで示したような歯の欠損した形の間欠歯車は軽い負荷＆遅い速度でのみ使える機構なのだと思います。

----
[[fusion360-study-gears チュートリアルへ戻る]](https://github.com/osamutake/fusion360-study-gears/blob/main/README-ja.md#チュートリアル)
