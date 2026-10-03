---
name: classroom-presentation-slides
description: >-
  課堂互動簡報產生器（Classroom Presentation Slides Generator）。專門將教師或使用者提供的各學科教學教材、主題情境或備課資料（國文、英文、數學、自然、社會、特教、SEL 社交情緒與人際溝通等），轉換為單一獨立且極簡滿版的「課堂互動簡報」HTML 檔案。核心特點：1.「極簡滿版舞台」：100vw × 100vh 滿版投影，無頂部/底部導覽條，溫潤暖米色背景（#f4efe6）搭配有機幾何柔光氣泡；2.「右下角懸浮藥丸控制盒」：預設半透明（opacity: 0.32），懸停平滑顯現，僅保留 ‹ X / Y › 換頁、九宮格目錄（O）與全螢幕（F）；3.「零 Emoji 雜訊」：嚴禁使用任何 emoji 圖示，遮罩顯答為純淨灰底「點擊顯答」，步驟以優雅中文序號呈現；4.「無感全鍵盤/翻頁筆支援」：←/→/Space/P/N 換頁、A 顯答、V 語音朗讀、O 目錄、B 黑屏、F 全螢幕。當使用者提到「課堂簡報」、「互動簡報」、「上課簡報」、「簡報模式」、「教學投影片」、「情境簡報」或要求生成簡報時，皆啟動此 skill。
---

# 課堂互動簡報產生器 (Classroom Presentation Slides Generator)

此技能專門將教師或使用者提供的教材、學科觀念、情境演練或課堂備課資料，轉換為**單一獨立、極致簡約且具備高度課堂互動性的「滿版課堂簡報」HTML 檔案**。

---

## 🎯 核心設計規範（Strict Requirements）

### 1. 滿版極簡舞台規範（Full-bleed Canvas）
- **滿版無導覽條**：視窗尺寸 `100vw × 100vh`，`overflow: hidden`，**絕對不放置傳統網頁的 Header 頂部導覽列、搜尋框、麵包屑或頁尾版權條**。
- **經典配色與氛圍底色**：
  - 背景色一律使用溫潤暖米色：`#f4efe6`。
  - 搭配 2～3 個半透明有機漸層柔光圓形（`.bg-circle-1, .bg-circle-2, .bg-circle-3`），營造沉浸式投影質感。
  - 核心點綴色：暖橘色 `#e07a42`（大字代碼、重點強調）、典雅深綠 `#2c5346` / `#e3ece7`（模組標籤）、深石板色 `#2c353d`（內文主色）。

### 2. 右下角懸浮藥丸控制盒（Minimalist Pill Controller）
- **固定位置**：固定於右下角 `fixed bottom-4 right-5 sm:bottom-6 sm:right-8 z-40`。
- **預設半透明設計**：
  - 滑鼠未懸停時：`opacity: 0.32`（半透明，完全不遮擋投影片底部的文字與卡片）。
  - 滑鼠懸停（Hover / Focus）時：平滑過渡至 `opacity: 1` 且微浮 `transform: translateY(-2px)`。
- **控制盒精簡內容（嚴禁加入多餘文字標籤）**：
  1. `‹`：上一頁按鈕
  2. `X / Y`：當前頁碼與總頁數（如 `1 / 8`，使用等寬字型 `font-mono`）
  3. `›`：下一頁按鈕
  4. 分隔線：`h-3.5 w-[1px] bg-white/20 mx-0.5`
  5. `⊞`：九宮格章節目錄開關（快捷鍵 `O`）
  6. `⛶`：全螢幕切換（快捷鍵 `F`）
- **嚴格禁止**：在藥丸盒內塞入「第一節」、「第二節」、「語音」、「顯答」等文字按鈕，保持極致俐落。

### 3. 零 Emoji 雜訊原則（Zero Emoji Clutter）
- **核心痛點**：過多 Emoji 會造成大螢幕投影視覺雜亂、學生注意力分散、失去專業教材質感。
- **嚴格規範**：
  - ❌ 嚴禁在步驟標題中使用 Emoji（如 🎬, 💓, ⚠️, 🤝, 💡, 🦔, 🕊️, 🗣️, 👀, 🚫, 🏆, 👉）。
  - ❌ 遮罩按鈕一律使用純淨文字：`點擊顯答`（禁止帶 💡）。
  - ❌ 警示框文字一律使用：`刺蝟話（你訊息）：`（禁止帶 🦔）。
  - ❌ 演練提示一律使用：`課堂演練：兩人一組，看著對方眼睛練習說說看`（禁止帶 🗣️）。
  - ✅ 一律改用純淨排版、清晰數字標號（如 `① 事實｜「我看見……」`、`1. 眼神堅定`）與細緻 FontAwesome 向量圖示。

### 4. 投影片經典結構標準（Slide Structure Standards）

#### A. 封面頁（Slide 0）
1. **頂部模組標籤**：綠色圓角膠囊（如 `• 模組一 ‧ 社交技巧與溝通`）。
2. **大字課程代號**：巨大醒目 `L1` 或單元號，暖橘色 `#e07a42`，字級 `text-5xl sm:text-7xl font-black font-display`。
3. **主標題與副標**：粗黑大標題（`text-3xl sm:text-6xl font-black`）＋ 導讀說明。
4. **左下方章節導航卡片**：2～3 張白底微陰影圓角卡片（顯示節次與核心主題），點擊可直接跳轉至該章節。

#### B. 情境演練／教學內頁（Slide 1 ~ N）
- **左右黃金分割（左 40% ~ 45%，右 55% ~ 60%）**：
  - **左欄**：情境標籤膠囊 ＋ 3D/實境插圖（`aspect-[16/10]` 圓角） ＋ 發生什麼事（客觀描述） ＋ 刺蝟話/錯誤示範對照警示盒。
  - **右欄**：
    - 主標題（如 `「我訊息」4 步驟口頭表達`）。
    - 4 步驟拆解卡片：`① 事實`、`② 感受`、`③ 影響`、`④ 期待`，關鍵詞與句子採用 `.answer-mask.hidden-ans` 點擊顯答遮罩。
    - 底部操作列：兩人一組演練提示 ＋ 「聽語音示範」按鈕。

#### C. 總結頁（Final Slide）
- 頂部通關膠囊 ＋ 實踐 3 大要訣卡片（純數字 1, 2, 3 圓圈標記） ＋ 結尾說明與自動彩帶慶祝（`confetti`）。
- **結尾純淨化**：不放置突兀的大跳轉按鈕，回歸沉浸式簡報體驗。

---

## ⌨️ 課堂快捷鍵配置（無感全鍵盤／翻頁筆支援）

簡報必須內建完整 `keydown` 事件監聽器：
- `ArrowRight` / `Space` / `PageDown` / `N`：下一頁
- `ArrowLeft` / `PageUp` / `P`：上一頁
- `A`：一鍵揭曉／隱藏本頁所有遮罩答案（Toggle All Answers）
- `V`：Web Speech 智慧語音朗讀本頁示範內容（台灣腔 `zh-TW`，語速 `0.92`）
- `O`：開啟／關閉九宮格章節目錄彈窗（Overview Modal）
- `B`：課堂黑屏模式（Blackout Layer）
- `F`：全螢幕切換（Fullscreen Toggle）

---

## 💻 完整單一 HTML 範本架構（Template Skeleton）

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>單元名稱｜課堂互動簡報</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Canvas Confetti -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;500;600;700;900&family=Plus+Jakarta+Sans:wght@700;800&family=JetBrains+Mono:wght@600;700&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['"Noto Sans TC"', '-apple-system', 'BlinkMacSystemFont', 'sans-serif'],
            display: ['"Plus Jakarta Sans"', '"Noto Sans TC"', 'sans-serif'],
            mono: ['"JetBrains Mono"', 'monospace'],
          },
          colors: {
            deck: {
              bg: '#f4efe6',
              accent: '#e07a42',
              slate: '#2c353d',
            }
          }
        }
      }
    }
  </script>

  <style>
    * { box-sizing: border-box; user-select: none; -webkit-user-select: none; }
    body {
      font-family: "Noto Sans TC", -apple-system, BlinkMacSystemFont, sans-serif;
      background-color: #f4efe6;
      color: #2c353d;
      margin: 0; padding: 0;
      width: 100vw; height: 100vh;
      overflow: hidden; position: relative;
    }

    /* 滿版氛圍氣泡 */
    .bg-circle-1 {
      position: absolute; right: 4%; top: 14%; width: 340px; height: 340px; border-radius: 50%;
      background: radial-gradient(circle, rgba(224, 122, 66, 0.16) 0%, rgba(224, 122, 66, 0.01) 70%);
      pointer-events: none; z-index: 1;
    }
    .bg-circle-2 {
      position: absolute; right: 12%; top: 26%; width: 440px; height: 440px; border-radius: 50%;
      background: radial-gradient(circle, rgba(79, 140, 125, 0.15) 0%, rgba(79, 140, 125, 0.01) 70%);
      pointer-events: none; z-index: 1;
    }

    /* 遮罩點擊顯答（無 emoji） */
    .answer-mask {
      position: relative; cursor: pointer; transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
      border-radius: 0.5rem; padding: 0.15rem 0.6rem; display: inline-block; vertical-align: middle;
    }
    .answer-mask.hidden-ans {
      background-color: #e5dfd5; color: transparent !important; border: 1.5px dashed #a89f91;
      min-width: 120px; text-align: center;
    }
    .answer-mask.hidden-ans::after {
      content: "點擊顯答"; position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%);
      color: #6e6456; font-size: 0.85rem; font-weight: 700; pointer-events: none; white-space: nowrap;
    }
    .answer-mask.hidden-ans:hover { background-color: #dbd4c8; border-color: #574e40; }
    .answer-mask.revealed-ans {
      background-color: #fef08a; color: #854d0e !important; font-weight: 700; border: 1.5px solid #facc15;
      animation: fadeIn 0.22s ease-out;
    }
    @keyframes fadeIn { from { opacity: 0.5; transform: scale(0.98); } to { opacity: 1; transform: scale(1); } }

    /* 投影片切換 */
    .slide-item { display: none; opacity: 0; transform: scale(0.99); transition: opacity 0.25s ease, transform 0.25s ease; width: 100%; height: 100%; }
    .slide-item.active { display: flex; opacity: 1; transform: scale(1); }

    /* 右下角懸浮藥丸控制盒 */
    .pill-controller {
      background: rgba(30, 36, 43, 0.88); backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px);
      box-shadow: 0 12px 28px -6px rgba(0, 0, 0, 0.28), 0 0 0 1px rgba(255, 255, 255, 0.1);
      opacity: 0.32; transition: opacity 0.3s cubic-bezier(0.4, 0, 0.2, 1), transform 0.2s ease;
    }
    .pill-controller:hover, .pill-controller:focus-within { opacity: 1; transform: translateY(-2px); }
    .pill-btn { transition: all 0.15s ease; }
    .pill-btn:hover { background-color: rgba(255, 255, 255, 0.15); color: #ffffff; }
    .pill-btn:active { transform: scale(0.94); }

    /* 黑屏 */
    #blackout-layer { display: none; position: fixed; inset: 0; background: #000000; z-index: 100; }
    #blackout-layer.active { display: block; }
  </style>
</head>
<body class="w-screen h-screen select-none overflow-hidden bg-[#f4efe6] flex flex-col justify-between">

  <div class="bg-circle-1"></div>
  <div class="bg-circle-2"></div>
  <div id="blackout-layer" onclick="toggleBlackout()"></div>

  <!-- 滿版投影片舞台 -->
  <main class="flex-1 w-full max-w-7xl mx-auto px-6 sm:px-12 py-6 sm:py-8 flex items-center justify-center relative z-10 overflow-hidden">
    <!-- Slide 0, Slide 1, ... -->
  </main>

  <!-- 右下角懸浮藥丸控制盒 -->
  <div class="fixed bottom-4 right-5 sm:bottom-6 sm:right-8 z-40">
    <div class="pill-controller text-white rounded-full px-2.5 sm:px-3 py-1 sm:py-1.5 flex items-center gap-1.5 sm:gap-2 text-xs sm:text-sm font-bold shadow-2xl">
      <button onclick="prevSlide()" class="pill-btn w-7 h-7 rounded-full flex items-center justify-center text-slate-300 hover:text-white" title="上一頁 (← / P)">
        <i class="fas fa-chevron-left text-xs"></i>
      </button>
      <div id="pill-slide-counter" class="font-mono text-xs sm:text-sm font-bold tracking-wider px-1 text-slate-200 min-w-[42px] text-center">
        1 / N
      </div>
      <button onclick="nextSlide()" class="pill-btn w-7 h-7 rounded-full flex items-center justify-center text-slate-300 hover:text-white" title="下一頁 (→ / N / 空白鍵)">
        <i class="fas fa-chevron-right text-xs"></i>
      </button>
      <div class="h-3.5 w-[1px] bg-white/20 mx-0.5"></div>
      <button onclick="toggleOverviewModal()" class="pill-btn w-7 h-7 rounded-full flex items-center justify-center text-slate-300 hover:text-white" title="章節目錄 (O)">
        <i class="fas fa-grip text-xs sm:text-sm"></i>
      </button>
      <button onclick="toggleFullScreen()" class="pill-btn w-7 h-7 rounded-full flex items-center justify-center text-slate-300 hover:text-white" title="全螢幕切換 (F)">
        <i class="fas fa-expand text-xs"></i>
      </button>
    </div>
  </div>

  <!-- 九宮格目錄彈窗 -->
  <div id="overview-modal" class="hidden fixed inset-0 z-50 bg-slate-900/80 backdrop-blur-md flex items-center justify-center p-6" onclick="closeOverviewIfBackdrop(event)">
    <!-- 目錄卡片網格 -->
  </div>

  <!-- 核心控制腳本 -->
  <script>
    // 投影片切換、語音朗讀、顯答遮罩、黑屏、全螢幕等邏輯
  </script>
</body>
</html>
```
