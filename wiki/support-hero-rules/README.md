# Support Hero Rules Guide | 助戰規則指南

Support Heroes let your Terminal User Network share elite operatives for dungeon squads. They consume shared Node Points, always use the owner's gear/skills, and obey the same mood limits as normal agents.

助戰英雄讓終端用戶網路共享菁英幹員，並可編入地下城隊伍。借用時會消耗網路節點點數，沿用原主的裝備／技能，且受心情規則限制。

---

## 📖 Overview | 概覽

- Share up to **two** heroes as network assets and borrow **one** per team / 最多分享 **2 名**英雄、每隊可借 **1 名**。
- Borrowed heroes act autonomously following the owner's loadout / 借出的英雄依原裝備及技能運作。
- Rewards always belong to the borrower while owners simply help the network / 獎勵歸借用者，所有者僅提供支援。

## 🔐 Requirements | 使用條件

1. **Join a Terminal User Network**; the preference toggle stays locked until membership is detected.
2. **Maintain Node Points**; each dungeon run with a support hero consumes **1 Node Point** when the run begins.
3. **Keep hero mood above 0**; heroes at 0 mood count as unassigned even if they sit in the support slot.
4. **Store heroes in Inventory**; heroes currently inside squads or workstation tasks cannot be nominated.

1. **加入終端用戶網路**：偵測到網路會員資格前，偏好設定中的開關會鎖定。
2. **保有節點點數**：每場帶助戰英雄的地下城在開場時消耗 **1 點**節點點數。
3. **維持心情 > 0**：心情歸零的英雄視同未派駐，即使放在助戰欄也無效。
4. **英雄需在背包**：已編隊或忙於工作站任務的英雄無法設定為助戰。

## 🛠️ Setting & Borrowing Flow | 設定與借用流程

### Setting Support Heroes | 設定助戰英雄
1. Open **Inventory → Heroes** and press **Set Support Heroes**.
2. Pick up to two candidates; confirming moves them into the network support roster.
3. Return to the same screen whenever you want to rotate contributors.

1. 進入 **背包 → 英雄**，點 **設定助戰英雄**。
2. 選擇最多兩名候選人，確認後加入網路助戰名單。
3. 需要時再次回到此畫面即可更換支援者。

### Borrowing Support Heroes | 借用助戰英雄
1. Form a dungeon team and tap the **Support Hero slot**.
2. Review available heroes, note the Node Point cost, and confirm the selection.
3. The borrowed hero joins only for the upcoming run; select again for future battles.

1. 組隊時點擊 **助戰槽**。
2. 檢視可借英雄與節點消耗後確認。
3. 借出的英雄僅陪同下一場戰鬥，後續需重新選擇。

## ⚙️ Preference Integration | 偏好設定整合

- The toggle **Settings → Gameplay → Use Support Hero by default** writes to `terminal-ark-preferences.gameplay.useSupportHero` so it syncs across sessions.
- When the toggle is disabled (not in a network), clicking it opens the Terminal Browser on this guide instead of displaying a plain message.

- 「設定 → 遊戲內容 → 預設啟用助戰英雄」會寫入 `terminal-ark-preferences.gameplay.useSupportHero`，跨會話同步。
- 未加入網路而被鎖定時，點擊會開啟終端瀏覽器，顯示本指南而非單純的提示文字。

## 💡 Tips & Troubleshooting | 技巧與疑難排解

- Node Points update instantly; if the pool hits 0 the support slot greys out until replenished.
- Heroes resting in the Lounge regain **10 mood/hour** from their current value—rotate depleted heroes before lending them.
- Leaving a network disables auto-usage and removes shared heroes; rejoin to re-enable.
- If Inventory shows “support slot locked,” ensure the hero is not assigned to squads or workstation duties.

- 節點點數即時更新；歸零時助戰槽會變灰，補足後才可再次借用。
- 休息室會以 **每小時 10 點** 從當前值恢復心情，借出前記得輪休。
- 離開網路會關閉預設助戰並撤回共享英雄，重新加入後再度啟用。
- 背包顯示「助戰槽鎖定」時，請確認英雄未在編隊或工作站任務中。
