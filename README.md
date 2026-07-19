# 價值產生器｜雲端部署

這個分支是「價值產生器」的獨立雲端部署版本，不會影響 `main` 分支原有內容。

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/xieyaozhong/-/tree/agent/value-generator-cloud)

## 部署時要做的事

1. 按上方 **Deploy to Render**。
2. 登入或建立 Render 帳號。
3. 在 `APP_PASSWORD` 輸入一組長且不重複的密碼。
4. 確認建立 Starter Web Service 與 1 GB Persistent Disk。
5. 部署完成後，以帳號 `admin` 和剛才設定的密碼登入。

## 已配置

- FastAPI + Docker
- 新加坡區域
- `/health` 健康檢查
- HTTP Basic Auth 登入保護
- SQLite 永久磁碟：`/app/data/value_generator.db`
- 自動部署預設關閉，避免未確認的更新直接上線

## 注意

這個應用需要持續執行夜間蒐集工作，並保存 SQLite 資料，因此 Blueprint 使用付費 Starter 執行個體與永久磁碟。Render 的免費服務會休眠，而且本機檔案不具永久性，不適合這個用途。
