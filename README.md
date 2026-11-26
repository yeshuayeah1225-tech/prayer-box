# RENEW 心事寄放所
第一版原型，尚未部署。管理帳號：yeshuayeah1225@gmail.com。

1. 使用教會 Google 帳號建立私人試算表，從「擴充功能 → Apps Script」貼上 gas/Code.gs，執行 setup 並授權。設定專案時區 Asia/Taipei。
2. 在 Apps Script 專案設定的指令碼屬性確認 RECIPIENTS（逗號分隔），設定 OPEN=true 才接受投稿。部署為網頁應用程式，以自己身分執行，存取權限為任何人（需確認帳號允許匿名）。複製 /exec 網址。
3. GitHub 建立公開 prayer-box repository，將前端檔案與 workflow 上傳。Settings → Pages 選 GitHub Actions；Settings → Secrets and variables → Actions → Variables 建立 VITE_GAS_URL，值為 /exec 網址。重新執行 workflow。不要將真實代禱資料放入 GitHub。
4. 使用無痕視窗與手機測試投稿、錯誤畫面、試算表及寄信；手動執行 notifyPending 測試通知。僅共用給指定同工，勿公開試算表。
5. 活動後設定 OPEN=false，依教會確認的期限清除資料與備份，移除通知觸發器。

限制：目前使用原生 HTML POST 導向 Apps Script 回覆頁，避免依賴跨網域 fetch；需實際驗證部署環境。蜜罐及全站每分鐘 30 筆上限只是基礎防護，正式公開前應加入伺服器端驗證的 CAPTCHA，避免惡意投稿與阻斷。通知為每 15 分鐘彙整，寄信成功但寫入通知時間失敗可能重複寄送。尚未確認資料保存期限、最終主視覺及同工名單。未執行 npm build 或線上整合測試。
