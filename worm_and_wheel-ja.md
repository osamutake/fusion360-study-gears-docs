# ウォームとウォームホイールを作り、組み合わせて動かしてみます。

[[fusion360-study-gears チュートリアルへ戻る]](https://github.com/osamutake/fusion360-study-gears/blob/main/README-ja.md#チュートリアル)

<a href="assets/worm-wheel15.gif"><img src="assets/worm-wheel15.gif" height="250" /></a>

## ウォームの生成

ウォームはラックを回転させることで生成しています。

Rack/Worm タブで Num. Spiral （条数）を 1 以上にするとラックではなくウォームが生成されます。

<a href="assets/worm3.png"><img src="assets/worm3.png" height="220" /></a>
<a href="assets/worm4.jpg"><img src="assets/worm4.jpg" height="220" /></a>

条数は、ウォームを１回転させたときに軸方向に進むピッチ数のことです。
ウォームの断面を見たときに円周上に並ぶ歯の数でもあります。

図は同じピッチ、同じ基準円直径で条数を１，２，３，４と変化させて生成したウォーム形状です。

## ウォームの印刷

ウォームの歯は大きく横に張り出しているため、3D プリンターでウォームを印刷するときは縦に２つに割って半分ずつ印刷して組み合わせるなどの工夫がいるようですね。

## ウォームホイールの生成

Cylinder タブの Worm Wheel にチェックを入れ、
Worm Diameter にウォームの基準円直径を、
Worm Spiral にウォームの条数を入力するとウォームホイールを生成できます。

<a href="assets/worm_wheel1.png"><img src="assets/worm_wheel1.png" height="250" /></a>

そのままの状態でウォームとかみ合う（あるいは半ピッチ分回転が必要かも）ように生成されるため、
そのままウォームと組み合わせて動かせるはずです。

ウォームホイールの歯形は単純なインボリュート曲線などで表すことはできない、複雑な形状となっています。

この複雑な歯形は、円盤状の部材を実際にウォームの歯形（の先端を少し延長したホブ）と組み合わせて、干渉する部分を取り除く、という、実際の歯切り工程をシミュレーションする計算によって求めています。

このスクリプトではワンクリックで歯形が生成されますが、中身ではかなり苦労しています💦

<a href="assets/worm-wheel16.jpg"><img src="assets/worm-wheel16.jpg" height="400" /></a>

## 歯あたりの確認

ウォームとウォームホイールをモジュール4でバックラッシュ -0.02 mm として生成して干渉部分を可視化した。

<a href="assets/worm-wheel17.gif"><img src="assets/worm-wheel17.gif" height="400" /></a>

このスクリプトで生成されるウォームとウォームホイールとがきれいに噛み合い、
ウォームホイールの厚さ方向全域に渡って接触が得られていることが分かります。

## 条数を変更

条数を１～４まで変えて作成してみました。

条数が大きくなるとウォームホイールの歯形はかなりひねくれてきますが、これでちゃんと噛み合うようです。

（どうも計算誤差で干渉する部分ができてしまうことがあるようなので、少しバックラッシュを大きめに取った方が良いかもしれません・・・）

<a href="assets/worm-wheel18.png"><img src="assets/worm-wheel18.png" height="170" /></a>
<a href="assets/worm-wheel19.png"><img src="assets/worm-wheel19.png" height="170" /></a>
<a href="assets/worm-wheel20.png"><img src="assets/worm-wheel20.png" height="170" /></a>
<a href="assets/worm-wheel21.png"><img src="assets/worm-wheel21.png" height="170" /></a>

----
[[fusion360-study-gears チュートリアルへ戻る]](https://github.com/osamutake/fusion360-study-gears/blob/main/README-ja.md#チュートリアル)
