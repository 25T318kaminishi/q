<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8" />
<title>P5.js 練習問題解答</title>
<script src="https://cdn.jsdelivr.net/npm/p5@2.0.3/lib/p5.min.js"></script>
</head>
<body>
<h1>P5.js 練習問題解答</h1>
<script>
function setup() {
createCanvas(320, 180);
noLoop(); // 描画は一度だけ
}

function draw() {
background(255);
stroke("black");
strokeWeight(0.1);
noFill();

const totalRectCount = 18;
const maxWidth = 320;
const maxHeight = 180;

// 色相の範囲
const startHue = 0; // 一番大きな長方形の色相
const endHue = 340; // 一番小さな長方形の色相
const hueStep = (endHue - startHue) / (totalRectCount - 1);

// 一番大きな長方形の左上座標
const originX = 0;
const originY = 0;

// 一番大きな長方形の幅と高さ
const baseWidth = maxWidth;
const baseHeight = maxHeight;

for (let i = 0; i < totalRectCount; i++) {
// 比率
const ratio = (totalRectCount - i) / totalRectCount; // 1.0 → 1, 0.0 → 18番目
// 長方形の幅と高さ
const rectWidth = baseWidth * ratio;
const rectHeight = baseHeight * ratio;

// 長方形の左上座標（右下に収まるため、右下座標を基準にして左上を計算）
const x = originX + (baseWidth - rectWidth);
const y = originY + (baseHeight - rectHeight);

// 色相の計算
const hue = startHue + i * hueStep;

// 塗りつぶしの色設定（HSL）
fill(hue, 50, 75); // L=75%、C=50%（HSLの彩度と輝度に相当）

// 長方形の描画
rect(x, y, rectWidth, rectHeight);
}
}
 </script>
  </body>
</html>
