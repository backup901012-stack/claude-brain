# 跨 Session 協作規範

> 所有 Claude Code session 必須遵守此規範

---

## 一、各 Session 的領地

每個 session 擁有自己的專案，**其他人不能碰**。

| Session | 擁有的 Repo | 擁有的本地資料夾 |
|:---|:---|:---|
| **綜合大腦** | jamie-common、jamie-dashboard | `claude-綜合大腦解決大方向問題/` |
| **宏觀日報** | daily-macro-report | `Claude-每日宏觀日報/` |
| **股票量化** | stock-quant-research | `Claude-股票量化數據研究網/` |
| **香港賽馬** | hk-racing-quant | `Claude-香港賽馬研究/` |
| **命理系統** | qimen-chumenji | `Claude-全方位命理系統/` |

**所有 repo 統一在 `backup901012-stack` 帳號下。**

---

## 二、綜合大腦的權限

### 可以做
- 設定任何 repo 的 GitHub Secrets
- 管理 Cloudflare D1 / R2 / Workers / Pages
- **只讀**檢查其他專案的狀態
- 寫修改請求（由 Jamie 轉派）
- 管理 jamie-common 和 jamie-dashboard 的程式碼

### 不能做
- 修改其他 4 個專案的任何檔案
- 對其他 4 個專案做任何 git 寫入操作
- 部署 stock-screening-api Worker（屬於股票量化）

---

## 三、需要跨專案修改時

```
綜合大腦發現問題
    ↓
分析根因，寫出建議方案
    ↓
寫入「跨專案修改請求.md」
    ↓
告知 Jamie
    ↓
Jamie 轉達給對應 session
    ↓
對應 session 自己決定怎麼改、自己 commit + push
    ↓
綜合大腦確認 + 更新日誌
```

---

## 四、共用資源

| 資源 | 管理者 | 使用者 |
|:---|:---|:---|
| GitHub Secrets | 綜合大腦 | 所有 session |
| Cloudflare D1 表結構 | 綜合大腦 | 所有 session（透過 API） |
| Cloudflare R2 bucket | 綜合大腦 | 所有 session（透過 API） |
| jamie-common 套件 | 綜合大腦 | 所有 session（pip install） |
| jamie-dashboard 前端 | 綜合大腦 | 所有 session（透過 API） |
| stock-screening-api Worker | 股票量化 session | 所有 session（透過 API） |
