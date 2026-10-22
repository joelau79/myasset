# 我的資產 (myasset)

個人資產記錄 repo — 由 🦞 龍蝦老大 (OpenClaw) 維護。

## 內容

| 檔案 | 說明 |
|------|------|
| `assets.json` | 資產明細（結構化） |
| `README.md` | 本文件 |

## 資料格式

`assets.json` 每個資產項：

```json
{
  "name": "資產名稱",
  "type": "stock | fund | cash | crypto | property | other",
  "currency": "HKD | USD | CNY",
  "quantity": 0,
  "cost_basis": 0,
  "current_value": 0,
  "notes": ""
}
```

## 更新

由 OpenClaw 自動同步，或手動編輯後 commit。
