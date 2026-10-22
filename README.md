# 我的資產 (myasset) — 有數-style 資產管理

由 🦞 龍蝦老大 (OpenClaw) 維護嘅個人資產追蹤 repo。數據源同「有數」App 結構對齊。

**Repo**: https://github.com/joelau79/myasset

## 檔案結構

| 檔案 | 說明 |
|------|------|
| `assets.json` | 主數據（資產 + 心願 + 設定 + 歷史） |
| `index.html` | 離線網頁版（無需安裝，雙擊即開） |
| `README.md` | 本文件 |

## 數據模型

```json
{
  "meta": { "currency": "MOP", "duration_unit": "天", "decimals": 2 },
  "categories": ["未分類", "電腦", ...],
  "assets": [
    {
      "id": "a1",
      "name": "mac studio 256",
      "price": 90000,
      "type": "asset",
      "purchase_date": "2023-10-21",
      "category": "電腦",
      "tags": ["工作"],
      "cost_rule": "per_day | per_use | custom",
      "target_daily_mode": "none | by_price | by_date | custom",
      "include_in_total": true,
      "include_in_daily": true,
      "pinned": true,
      "retired": false,
      "sold": false
    }
  ],
  "wishes": [],
  "history": []
}
```

## 核心計算

- **總資產** = 所有 `include_in_total=true` 且未退役/未賣出 嘅 `price` (或 `market_value`) 加總
- **日均成本** = `price / 服役天數`，只計 `include_in_daily=true`
- **服役天數** = 今天 − `purchase_date`
- **目標日均** = `price / (target_end_date − purchase_date)`，用嚟計「還剩 X 天」

## 目前資產 (2026-10-22)

| 名稱 | 價格 | 購買日期 | 服役 | 日均 |
|------|------|---------|------|------|
| mac studio 256 | MOP$90,000 | 2023-10-21 | 1097 天 | 82.04 |
| serena c26 | MOP$250,000 | 2015-11-10 | 3999 天 | 62.51 |
| iphone 17 pro max | MOP$12,280 | 2025-10-17 | 370 天 | 33.18 |
| 極核 AE7Pro | MOP$21,000 | 2026-07-05 | 109 天 | 192.66 |
| 結他 | MOP$2,100 | 2026-08-15 | 68 天 | 30.88 |

**總資產**: MOP$375,380.00 · **日均成本**: MOP$401.28

## 更新方式

```bash
# 改 assets.json 之後
python3 /home/joehome/.openclaw/scripts/sync_myasset.py
```

或者直接喺 Telegram 同我講「更新 myasset：XXX」，我自動改 + push。
