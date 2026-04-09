# TikTok Shopセミナースライド

## CSS注意事項

このプロジェクトのスライドHTMLには「Readability overrides for 30-60代」として以下のCSSルールが存在する:

```css
.slide-content .card p,
.slide-content .card div p {
  color: #444 !important;
}
```

**インラインスタイルで`color`を変更しても反映されない。** `!important`がインラインスタイルを上書きするため。

### 対処法

1. ダーク背景のカードには `dark-card` クラスを付与する
2. 上書きルールの詳細度を元ルール以上にする（`.slide-content .card.dark-card div p` のように）
3. `getComputedStyle` で実際の適用色を確認する
4. 変更後はスクリーンショットで目視確認してから報告する

### 詳細度の注意

元ルール: `.slide-content .card div p { color: #444 !important; }` → 詳細度 0-2-2
上書き: `.slide-content .card.dark-card div p { color: #fff !important; }` → 詳細度 0-3-2（勝つ）
NG例: `.dark-card p { color: #fff !important; }` → 詳細度 0-1-1（負ける）
