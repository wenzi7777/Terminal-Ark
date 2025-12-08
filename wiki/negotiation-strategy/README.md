# Negotiation Strategy Guide | 談判策略指南

Negotiation Strategies decide which contracts your Trading Station accepts, letting you steer production toward Memory-rich info trades or Cache-heavy convoys while keeping the workstation in sync with your preferences.

談判策略決定貿易站接取的訂單種類，可依需求專注於 Memory 型資訊交易或高收益的 Cache 押運，並與偏好設定保持同步。

---

## 📖 Overview | 概覽

- Configure a **default strategy** so every workstation session starts with the correct focus.
- Swap strategies before queueing new orders; in-progress orders keep their existing type.
- Disabled controls (no workstation or no trading station) launch this guide in the Terminal Browser instead of showing a plain modal.

- 設定**預設策略**，讓每次開啟工作站都保持正確方向。
- 在排訂單前可隨時切換策略；進行中的訂單不會自動變更。
- 若尚未開啟工作站或建造貿易站，點擊鎖定的控制項會透過終端瀏覽器顯示本指南，而非一般訊息。

## 🔐 Unlock Requirements | 解鎖條件

1. **Initialize the Agent Workstation** via the Super Terminal storyline steps.
2. **Construct at least one Trading Station**; otherwise negotiation settings remain disabled.
3. **Assign an agent with mood > 0** so orders can be executed; agents at 0 mood count as absent.
4. **Power the facility** by running the Nuclear Plant/Super Terminal pair.

1. 透過超級終端劇情**完成代理人工作站初始化**。
2. **建造至少一座貿易站**，否則談判設定會鎖定。
3. **派駐心情 > 0 的代理人**，心情歸零視同未派駐。
4. 透過核電廠與超級終端供電，保持設施上線。

## ♟️ Strategy Types | 策略類型

| Strategy 策略 | Contracts 訂單內容 | Rewards 主要收益 | Recommended Scenarios 建議時機 |
| --- | --- | --- | --- |
| Assist Investigation 協助調查 | Memory-focused Info Trade orders | Memory, clue fragments, workstation EXP | Daily farming, leveling new cities, stockpiling crafting currency |
| Classified Intel 絕密資訊 | Cache-heavy Classified Convoy orders | Cache, Negotiation Chips, contact reputation | Preparing for premium kiosks or limited events |

## ⚙️ Preference Integration | 偏好設定整合

- Open **Settings → Agent Workstation → Default Trading Strategy** to choose a permanent preference stored inside `terminal-ark-preferences.workstation.tradingStrategy`.
- When a user lacks a workstation or trading station, the selector is grayed out; clicking it opens this guide in the Terminal Browser to explain the prerequisites.

- 透過 **設定 → 代理人工作站 → 預設談判策略** 指定永久偏好，寫入 `terminal-ark-preferences.workstation.tradingStrategy`。
- 尚未解鎖時選單會變灰，點擊後會在終端瀏覽器開啟本指南，說明達成條件。

## 🏭 Using Strategies In-Game | 遊戲內使用方式

1. Enter the Agent Workstation, select a Trading Station slot, and ensure an agent with mood > 0 is on duty.
2. The saved default strategy pre-fills the **Negotiation Strategy** selector; adjust it before starting new orders.
3. Empty order slots adopt the currently selected strategy, while existing orders finish under their original rules.
4. Cancel and recreate orders if you must pivot immediately after a strategy change.

1. 進入代理人工作站，選擇貿易站插槽並確保有心情 > 0 的代理人值勤。
2. 儲存的預設策略會預填「談判策略」下拉，開始新訂單前可自行調整。
3. 空白訂單槽會按照當前策略生成，而既有訂單會沿用既定類型。
4. 若切換後需要立即生效，請取消舊訂單並重新建立。

## 💡 Tips & Troubleshooting | 技巧與疑難排解

- Orders cannot start if the workstation reports "operations locked" (no agent, 0 mood, or power outage). Resolve those warnings first.
- Switching strategies while orders are running only affects future slots; cancel unwanted ones to pivot quickly.
- Clearing browser cache does **not** remove the preference because it lives in `terminal-ark-preferences`.
- Missing workstation data (API errors) is treated as "not initialized"—reopen the popup after relogging if detection fails.

- 當工作站顯示「無法操作」（無人、心情歸零、停電）時，訂單無法啟動，請先排除異常。
- 進行中的訂單不會因此自動轉換；若要迅速轉向，請取消後重建。
- 即使清除瀏覽器快取，設定仍保存在 `terminal-ark-preferences` 內。
- 工作站狀態查詢失敗時會視為「未初始化」，重新登入並再打開設定即可重試。
