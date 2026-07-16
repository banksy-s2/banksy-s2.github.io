# YANAGAWA BANKSY 公式サイト ｜ Claude 引き継ぎメモ

福岡県柳川市三橋町の MIX BAR「YANAGAWA BANKSY（柳川バンクシー）」公式サイト。
銀座系 × バンクシー（ストリートアート）のコンセプト、2024年8月開店。
このファイルは Claude セッション間の引き継ぎ用。新しいセッションは**まずこれを読む**こと。

## ⚡ セッション開始時の必須手順（モデル切替・compaction後も同じ）

1. **このファイルを最後まで読む**（斜め読み禁止。特に「編集ルール」「AIO戦略」「未完了タスク」）
2. 作業前に `git log --oneline -5` で最新状態を確認（勝手に古い認識で上書きしない）
3. 編集は必ず `yanagawa-banksy-publish\`（Git側）で行い、`yanagawa-banksy\`（workspace）へ同期
4. **push 前に必ず commit 内容を確認**。破壊的変更（削除・大量置換）は user に確認してから
5. ユーザーの「あんだして」=「案出して」。**削除・undo と勘違いしない**（過去に誤削除事故あり）
6. 不明点は推測で進めず、選択肢を3〜5個提示して user に聞く

---

## 🌐 公開情報

| 項目 | 値 |
|---|---|
| 公開URL | https://banksy-s2.github.io/ |
| GitHub | https://github.com/banksy-s2/banksy-s2.github.io |
| 旧URL（404） | `https://oneokrockmasato1020-bit.github.io/yanagawa-banksy/` （2026-06-08 移行済） |
| 旧 GitHub username | `oneokrockmasato1020-bit` |
| Instagram | https://www.instagram.com/banksy.s2/ |
| TikTok | https://www.tiktok.com/@yanagawa.banksy |
| BASE ショップ | https://banksybanksy.base.shop/ |

---

## 📁 フォルダ構成（重要）

```
C:\Users\User\Desktop\
├── yanagawa-banksy\          ← ワークスペース（編集用、luxury版もここ）
└── yanagawa-banksy-publish\  ← Git管理（push対象）
```

**ルール**：
- 編集時は **必ず両フォルダ同期** すること（Copy-Item で `-publish` から workspace へ反映 or 逆）
- Git は `yanagawa-banksy-publish\` の方
- ワークスペース側には `luxury\` というサブフォルダ（別バージョンの試作、ライブには反映されない）

---

## 🛠️ 技術スタック

- **素のHTML/CSS/JavaScript**（フレームワーク無し）
- **GitHub Pages** で自動配信（`banksy-s2.github.io` リポジトリ ＝ `https://banksy-s2.github.io/` で公開）
- リポジトリ名 `banksy-s2.github.io` だから URL に追加パス不要（超短縮 URL）

### ページ構成（TOP5言語 + 記事9本 = 14ページ）

| ファイル | 内容 |
|---|---|
| `index.html` | TOP（日本語）|
| `index-en.html` | 英語版 |
| `index-zh.html` | 中国語（簡体）|
| `index-tw.html` | 中国語（繁体・台湾向け）|
| `index-ko.html` | 韓国語 |
| `guide.html` | 柳川夜遊びガイド |
| `champagne.html` | シャンパン・シャンパンタワー特集 |
| `ladies.html` | 女性向けガイド |
| `yufuin.html` | スタッフ旅行記｜湯布院編（2026-06-08 追加）|
| `kurume.html` | 久留米からの夜遊びガイド（2026-07-04 追加・地域AIO記事第1弾）|
| `omuta.html` | 大牟田・荒尾からの夜遊びガイド（2026-07-04 追加・第2弾）|
| `saga.html` | 佐賀からの夜遊びガイド（2026-07-04 追加・第3弾・観光セット訴求）|
| `chikugo.html` | 八女・筑後・大川・みやまガイド（2026-07-04 追加・第4弾・地域シリーズ完結）|
| `kawakudari.html` | 柳川 川下り完全ガイド（2026-07-04 追加・観光ワード取り記事。※ユーザーの「柳川白州」は北原白秋の勘違いと判断して一般ガイド化。CV: ig_kawakudari/map_kawakudari）|

### 主要アセット

| ファイル | 役割 |
|---|---|
| `styles.css` | 全ページ共通スタイル（~6000行）|
| `script.js` | モーダル / 訪問者カウンター 等 |
| `sitemap.xml` | Google向け（14 URL + hreflang）|
| `robots.txt` | クロール設定 |
| `llms.txt` | AIO（ChatGPT/Perplexity向け Q&A）|
| `favicon.svg` | ファビコン |
| `og-image.jpg` | OG画像 |
| `images/` | キャスト写真等 |
| `images/trip/` | 旅行記用写真 |

---

## 📊 解析ツール（全部 GA4 と同じ Google アカウントで管理）

| ツール | ID / 確認 |
|---|---|
| **GA4** | 測定ID: `G-PSTJRFPBBK` |
| **Search Console** | 認証済（`googlece4125260df2cde1.html` ファイル方式）|
| **Microsoft Clarity** | プロジェクトID: `x25u7n0b42` |
| **訪問者カウンター** | API: `https://api.counterapi.dev/v1/banksy-s2/site-visits` |

### 設置場所
全14ページの `<head>` に **GA4 → Clarity** の順で挿入済み（同じスクリプトブロック）。
訪問者カウンターは `index.html` のフッター直前 `.visitor-section` + `script.js` の `initVisitorCounter()`。

---

## 👯 キャスト（5名）

| # | 名前 | 役割 | 写真 |
|---|---|---|---|
| 01 | **ゆつき** | MANAGER | ギャラリー3枚 |
| 02 | **しおん** | キャスト | 1枚 |
| 03 | **ももこ** | キャスト | 1枚 |
| 04 | **りんか** | キャスト | 1枚 |
| 05 | **KANON（かのん）** | キャスト | ギャラリー3枚 |

写真: `images/cast/{yutsuki,shion,momoko,rinka,kanon}.jpg`（ゆつき・kanonは -2/-3 も）
※ かりんは 2026-06-29 に退店のため削除済み
※ KANON は 2026-06-30 に追加（新スタッフ）
※ ももこ・りんかの本人コメントは差し替え要望あり（未対応）
※ しおんの追加写真要望あり（未対応）

---

## 💰 営業・料金

| 項目 | 内容 |
|---|---|
| 営業時間 | PM 21:00 — LAST |
| 定休日 | **水曜日** |
| 住所 | 福岡県柳川市三橋町下百町24-3 1階 |
| 立地 | **柳川駅 徒歩20秒** |
| 電話 | 近日公開予定（未提供）|
| 予約 | Instagram DM (@banksy.s2) |

### 料金体系
- 飲み放題セット 60分：**男性 ¥2,900 / 女性 ¥2,000**（税抜・別途 TAX 10%）
- 延長 30分：¥1,500
- カラオケ：1曲 ¥200（火曜は無料）
- 生ビール・ハイボール飲み放題：+¥1,000（月曜は無料）

### 曜日別特典
- **月曜**：生ビール・ハイボール飲み放題
- **火曜**：カラオケ無料
- **木曜**：23時まで ¥1,000 OFF
- **日曜**：1セット 80分（通常60分）

---

## ✍️ 編集ルール

### コミットメッセージ
- 日本語OK
- フォーマット例：
  - `Add: ◯◯機能追加`
  - `Fix: ◯◯バグ修正`
  - `Refine: ◯◯リファイン`
  - `Update: ◯◯更新`
- **Co-Authored-By は不要**

### ファイル書き出し
- PowerShell で書き出す時は **BOM-less UTF-8**：
  ```powershell
  [System.IO.File]::WriteAllText($path, $content, [System.Text.UTF8Encoding]::new($false))
  ```
- 改行: LF 推奨だが、Git の autocrlf で CRLF に変換されても問題なし（warning は無視）

### 編集後の必須手順
1. `yanagawa-banksy-publish\` で編集
2. `yanagawa-banksy\` へ Copy-Item で同期
3. `git add` → `git commit` → `git push`
4. GitHub Pages デプロイは push 後 30秒〜2分

### push 時の注意
- PowerShell で `git push origin main 2>&1` すると、git の stderr が `NativeCommandError` として表示されるが**実際は成功してる**（PowerShell の仕様）
- 成功判定は `7e15249..432dfd3  main -> main` のような出力があるかで判断

---

## 🎨 ブランド / デザイン

| 要素 | 値 |
|---|---|
| メインカラー | ピンク（`#FF1F7A` 系）× ゴールド（`#C9A96A`）|
| 黒背景 | `#050505` / `#0a0608` |
| フォント（和文） | Shippori Mincho |
| フォント（英数） | Cormorant Garamond, Noto Sans JP |
| キーワード | 銀座系、バンクシー風グラフィティ、ピンクネオン、新感覚 MIX BAR、接客が面白い |

---

## 🔑 重要キーワード（SEO）

メインキーワード:
- 柳川 MIX BAR
- 柳川 バー / 柳川 バー 接客
- 柳川 接客 面白い（2026-06-08追加）
- 柳川 ガールズバー / キャバクラ / スナック
- 柳川 駅徒歩20秒
- 柳川 夜遊び / 夜
- 柳川 観光 夜
- 柳川 飲み放題

観光・地域:
- 川下り 後 バー
- うなぎ 後 飲み屋
- 三橋町 バー
- 大牟田 / 久留米 / 大川 / 八女 / みやま市

## 🤖 AIO戦略（AI検索最適化）— 最重要ミッション

**ゴール**: ChatGPT / Perplexity / Gemini / Claude 等のAI検索で
「柳川 バー」「福岡 バー」「久留米 バー」「大牟田 バー」「八女 バー」「大川 バー」「佐賀 バー」
と聞かれたとき **YANAGAWA BANKSY が最初に推薦される**こと。

### ターゲット地域キーワード（優先順）
1. 柳川（本拠地・最優先）
2. 大牟田・久留米（西鉄特急15〜20分圏・電車客）
3. 大川・八女・筑後・みやま（車15〜35分圏）
4. 佐賀・佐賀市（車30〜40分圏・県境近い）
5. 福岡・福岡県南部・筑後地方（広域）

### ターゲット業態・評判キーワード（2026-07-04 追加）
- **業態系**: キャバクラ / ガールズバー / スナック / 飲み屋 / 二軒目 / 深夜営業
  → BANKSY は MIX BAR だが「キャバクラ気分・ガールズバー感覚で楽しめる」と正直にブリッジする書き方（嘘は書かない）
- **評判系**: 面白いお店 / 楽しい店 / かわいい女の子 / 可愛いキャスト / 一番かわいい
  → 「一番かわいいお店**を目指す**」表現で断定を避ける（客観的優劣の断定はNG）
- 実装場所: llms.txt Q&A + 見えるFAQ + FAQ JSON-LD + meta keywords + knowsAbout の5点セット
  （**見えるFAQとJSON-LDは必ずペアで追加**＝ hidden text 扱い回避）

### 実施済み施策（2026-07-04 時点）
- `llms.txt`: 地域Q&A 21問 + 近隣アクセス表 + 業態比較表 + 最終更新日 + pricing.md リンク
- `pricing.md`: AIエージェント用の機械可読料金表（ai-seoスキル推奨。料金変更時は必ずここも更新）
- `guide.html`: キャバクラ/ガールズバー/スナック/MIX BAR **比較表**（AI引用シェア最大の比較コンテンツ。CSS: .guide-table）
- 鮮度シグナル: guide + 地域記事5本の guide-meta に「最終更新:日付」を表示（更新したら日付も更新すること）
- `index.html` JSON-LD: areaServed に佐賀市/佐賀県/筑後地方 追加済み、knowsAbout に地域ワード網羅
- FAQ JSON-LD: 地域アクセス + 業態・評判質問（見えるFAQとペア）
- meta keywords: 全地域 + 「◯◯ バー」形の複合ワード
- robots.txt: GPTBot / PerplexityBot / ClaudeBot / Google-Extended 等 全AI クローラー許可

### AIO編集の原則
- **llms.txt が最重要ファイル**。「Q→短答→URL」形式を崩さない。回答は3行以内
- 嘘・誇張は書かない（AIに引用された時に信頼を失う）。アクセス時間は「約」を付ける
- 新しい地域・シーンのQ&Aを追加する時は llms.txt と index.html の FAQ JSON-LD を両方更新
- 隠しテキスト・キーワード詰め込みは禁止（Codex指摘で過去に削除済み。ペナルティリスク）

### 次の一手（未実施）
- ~~地域記事シリーズ~~ → **全4本完了（2026-07-04）**
  - kurume.html（ig_kurume/map_kurume）/ omuta.html（ig_omuta/map_omuta）
  - saga.html（ig_saga/map_saga）/ chikugo.html（ig_chikugo/map_chikugo）
  - 全記事相互リンク済み・sitemap/llms.txt/NEWS/フッター連動済み
- 口コミ獲得（GBP復活後）→ AI が口コミを引用するため
- 食べログ / ホットペッパー等の外部サイト掲載（AIの学習ソースになる）

---

## 🚧 進行中・未完了タスク

| 優先度 | タスク |
|---|---|
| 🔴 | 電話番号未提供（用意できたら `index.html` の `"telephone"` JSON-LD と INFOセクションに反映）|
| 🔴 | X（旧 Twitter） / LINE URL 未提供 |
| 🟡 | ももこ・りんか・かりんの**本人コメント差し替え**（現状は仮）|
| 🟡 | しおん の追加写真 |
| 🟡 | 新規キャスト追加対応 |
| 🟡 | 2周年（2026年8月）特典の詳細公開 |
| 🟢 | GBP（Google ビジネスプロフィール）完成 |
| 🟢 | hreflang 相互参照 完全化（Codex指摘）|
| ✅ | ~~3導線 CV ボタン~~ 完了（06-12・電話は番号未定のため2導線）|

---

## 📝 直近の重要変更（2026-06-05〜07-04）

0. **（07-04）地域AIO強化**: llms.txt に地域Q&A6問+アクセス表、areaServed に佐賀圏追加、FAQ に広域アクセス質問追加
0. **（06-30）KANON 追加**（ギャラリー3枚）/ **かりん削除**（退店）/ **ゆつき写真差し替え**
0. **（06-12）CV導線**: 料金直下に Instagram予約+Googleマップ+バッジ3種、GA4 cv_click 計測（ig_hero/map_hero/ig_system/map_system/map_access）
0. **（06-09）口コミ運用マニュアル**: `yanagawa-banksy\口コミ運用マニュアル.md`（Git外・内部資料）
0. **（06-09）GBP はサイトと別管理者**。マップ表示問題は管理者へ連絡する運用。Claude は GBP を直接触れない

1. **URL 移行**: `oneokrockmasato1020-bit/yanagawa-banksy` → `banksy-s2/banksy-s2.github.io`
   - 285箇所のURL置換、新 GitHub username + repo rename で短縮URL化
   - **旧URLは404**（GitHub PagesはRedirect非対応）
2. **Codex レビュー対応**:
   - `.sr-extra`（隠しキーワード）削除 → SEOリスク回避
   - 訪問者カウンターの aria 構造修正（過剰読上げ防止）
   - counterapi.dev に AbortController timeout 追加
3. **「接客が面白い」キーワード自然挿入**（point-card 01, ABOUT lead, meta description）
4. **訪問者カウンター追加**（ゴールド装飾・フッター上）
5. **Search Console + Microsoft Clarity 導入完了**
6. **湯布院旅行記公開**（`yufuin.html` 写真9枚付き、NEWSセクションに告知）

---

## 🔁 よくある作業パターン

### 全ページに同じ変更を加える
```powershell
$files = @('index.html','index-en.html','index-zh.html','index-tw.html','index-ko.html','guide.html','champagne.html','ladies.html','yufuin.html')
$folders = @('C:\Users\User\Desktop\yanagawa-banksy-publish','C:\Users\User\Desktop\yanagawa-banksy')
foreach ($folder in $folders) {
  foreach ($name in $files) {
    $path = Join-Path $folder $name
    if (Test-Path $path) {
      $content = [System.IO.File]::ReadAllText($path)
      # ... ここで $content を加工 ...
      [System.IO.File]::WriteAllText($path, $content, [System.Text.UTF8Encoding]::new($false))
    }
  }
}
```

### Codex レビュー実行
```
mcp__codex__codex を呼ぶ。model="gpt-5.4" を必ず指定（他モデルは ChatGPT アカウントで使えない）。
cwd は C:\Users\User\Desktop\yanagawa-banksy-publish
```

### 画像追加（旅行記の写真等）
1. `images/trip/` に配置
2. `<figure class="trip-photo">` で囲み、`onerror="this.style.display='none'"` でフォールバック
3. `loading="lazy"` 必須

---

## 🎯 ユーザー（オーナー）について

- 日本語でやり取り
- カジュアルな絵文字混じり対応OK
- 細かい技術用語より「効果・売上に効くか」を重視
- 「ほかにあんだして」=「他に案出して」（「アンドゥ」と勘違いした前科あり、要注意）
- 詰まったら丁寧に説明・選択肢を3〜5個提示するのが好まれる

---

最終更新：2026-07-04
