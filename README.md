# 賀卡快速排版列印工具

一個純前端的賀卡排版／列印小工具：選卡片尺寸、填文字，版位就會依照燙金花邊與「祝」字的固定位置自動避開，字體大小依字數自動縮放，也可以手動微調每個欄位的位置、大小、粗體、字型與對齊方式。設定好的版位會存在瀏覽器裡，下次打開同一台電腦、同一個瀏覽器會自動套用。

不需要後端、不需要建置工具，單一個 `index.html` 就能跑。

## 本機開啟

直接用瀏覽器打開 `index.html` 即可使用，或用任何簡單的靜態伺服器：

```bash
python3 -m http.server 8000
# 然後瀏覽器開 http://localhost:8000
```

## 放到 GitHub Pages

1. 建一個新的 GitHub repository，把這個資料夾裡的檔案（至少 `index.html`）推上去：

   ```bash
   git init
   git add .
   git commit -m "Init card template tool"
   git branch -M main
   git remote add origin https://github.com/<你的帳號>/<repo名稱>.git
   git push -u origin main
   ```

2. 到 repository 的 **Settings → Pages**。
3. **Source** 選擇 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，按 **Save**。
4. 等 1–2 分鐘，GitHub 會給你一個網址，通常是：

   ```
   https://<你的帳號>.github.io/<repo名稱>/
   ```

之後每次 `git push` 更新 `index.html`，網站會自動重新部署，不需要額外設定 GitHub Actions。

## 關於「儲存版位」

按「儲存這個尺寸的版位」時，設定是存在**目前這台裝置、這個瀏覽器**的本機儲存空間（localStorage）裡，不會上傳到 GitHub、也不會同步到其他裝置或瀏覽器。也就是說：
- 同一台電腦、同一個瀏覽器下次打開網站，會自動套用你上次存的版位。
- 換一台電腦、換瀏覽器、用無痕視窗，或清除瀏覽器資料，都需要重新校正一次。

如果之後需要多人共用同一組版位，可以考慮把版位改存成一個 JSON 檔案放進 repo 裡，再由網頁讀取——需要的話可以再請我加上。

## 列印注意事項

列印對話框中請將：
- 紙張大小設為與卡片相同的自訂尺寸
- 縮放比例設為 100%（不要用「配合頁面大小」）
- 邊界設為「無」

才能對準卡片本身固定的花邊與燙金字位置。

## 檔案結構

```
.
├── index.html   # 工具本體（唯一必要的檔案）
├── README.md    # 本說明文件
└── LICENSE      # MIT 授權
```
