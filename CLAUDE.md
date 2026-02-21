# MindMap Maker

純前端的 Markdown 心智圖編輯器，無需建置步驟。

## 專案結構

```
index.html          # 主應用程式（單一 HTML 檔案，包含所有 CSS/JS）
mindmap/            # 範例 .md 檔案資料夾
  app.js            # 另一版本的應用程式邏輯
  index.html        # 另一版本的入口頁面
  styles.css        # 另一版本的樣式
```

## 技術棧

- **CodeMirror 5** — Markdown 編輯器
- **Markmap** (`markmap-view`, `markmap-lib`) — 心智圖渲染
- **D3 v7** — Markmap 依賴
- **Marked** — Markdown 轉 HTML 預覽
- 所有函式庫皆透過 CDN 載入，無需 npm/build

## 瀏覽器限制

需要 **File System Access API**，僅支援 Chromium 系列（Chrome、Edge）。
Firefox / Safari 無法正常使用。

## 本機啟動

```bash
python3 -m http.server 8080
# 開啟 http://localhost:8080
```

## 主要功能

- 開啟整個資料夾，遞迴讀取 `.md` 檔案
- 側邊欄搜尋與切換檔案
- 左側 CodeMirror 編輯器，右側即時心智圖預覽
- 點擊心智圖節點可直接 inline 編輯，自動同步回編輯器
- Ctrl+S / Cmd+S 儲存，寫回本機檔案
- 支援心智圖 / 文章預覽兩種模式切換

## 修改注意事項

- `index.html` 是單一檔案應用，CSS 在 `<style>`，JS 在 `<script>`，直接修改即可
- Markmap 實例（`mm`）切換預覽模式時會重建，避免殘留舊資料
- 預覽更新有 300ms debounce（`schedulePreviewUpdate`）
