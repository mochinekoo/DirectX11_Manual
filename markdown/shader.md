# HLSLの関数
* dot
* saturate
* lerp

# エフェクト
* グラデーション
* セピア
  * r = 元の色のR * 0.393 + 元の色のG * 0.769 + 元の色のB * 0.189
  * g = 元の色のR * 0.349 + 元の色のG * 0.686 + 元の色のB * 0.168
  * b = 元の色のR * 0.272 + 元の色のG * 0.534 + 元の色のB * 0.131
  * saturateで、計算結果を1.0に収める
  * lerp(元の色, セピア後の色, セピアの強さ) でセピアの強さの色を求める
    * (r,g,bそれぞれに) 元の色 * (1.0f - セピアの強さ) + セピアの色 * セピアの強さ
```hlsl
        float3 original = color.rgb;
        float3 sepia;
        sepia.r = dot(original, float3(0.393, 0.769, 0.189));
        sepia.g = dot(original, float3(0.349, 0.686, 0.168));
        sepia.b = dot(original, float3(0.272, 0.534, 0.131));
        sepia = saturate(sepia);
        color.rgb = lerp(original, sepia, saturate(sepiaStrength));
```
* トライノーン
* 色調補正（明るさ、コンスラスト、色相、輝度、彩度）
* 色反転
```hlsl
        color.r = 1.0f - color.r;
        color.g = 1.0f - color.g;
        color.b = 1.0f - color.b;
```
* ディザリング
* モザイク
* ぼかし
* シャプ化

## 光
* エッジ発光
* ゴッドレイ
* 光条
* 拡散光
* 放射光

## 
* ランバート
* フォン
* バンプ
* ビルボード
* UVスクロール
