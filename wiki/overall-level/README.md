# Overall Level | 綜合等級

Overall Level is your account-wide equipment progression level for neural-connection AFK rewards. It is informational outside AFK: it appears on player profiles, Archive, and rankings, but it does not estimate Signal Dive combat strength.

綜合等級是帳號共用裝備用於神經連接 AFK 收益的進度等級。在 AFK 以外只作為資訊，顯示於玩家資料、Archive 與排行榜；它不代表訊號深潛戰鬥力。

---

## What Affects It | 影響因子

- The equipped upper and lower armor levels.
- The levels of valid upgrade modules installed in each armor.
- Empty armor sides, empty sockets, missing modules, and invalid modules count as level 0.
- Hero Rank, attunement, team profile, equipment rarity multipliers, quality, affixes, and carried consumables do not affect it.

- 已裝備的上身與下身裝甲等級。
- 實際插入每件裝甲的有效升級模組等級。
- 缺少護甲、空插槽、遺失模組或無效模組均以 Lv.0 計算。
- 英雄 Rank、同調、隊伍 Profile、裝備稀有度倍率、品質、詞綴與帶入消耗品皆不影響。

## How It Is Calculated | 計算方式

Each armor side assigns 80% of its score to the armor level and 20% to the average module level. The module average always divides by that armor's available socket capacity, so every empty socket contributes level 0.

每側裝甲的分數由護甲等級占 80%，模組平均等級占 20%。模組平均固定除以該護甲的可用插槽容量，因此每個空插槽都會貢獻 Lv.0。

```text
module average = sum(valid installed module levels) / armor socket capacity
side level = armor level × 0.8 + module average × 0.2
overall level = max(1, floor((upper side level + lower side level) / 2))

模組平均等級 = 有效已安裝模組等級總和 / 護甲插槽容量
單側等級 = 護甲等級 × 0.8 + 模組平均等級 × 0.2
綜合等級 = max(1, floor((上身等級 + 下身等級) / 2))
```

When both armor pieces and every socketed module are level 30, Overall Level is 30. Two level 30 armor pieces without modules produce Overall Level 24.

上下身護甲及所有插槽模組都是 Lv.30 時，綜合等級為 30；兩件 Lv.30 護甲完全沒有模組時，綜合等級為 24。

## AFK Rewards | AFK 收益

Neural-connection AFK uses the lower of Overall Level and the destination area's maximum level. The server recalculates the value when AFK starts; client previews are not trusted as authority. Overall Level itself has no hard upper limit.

神經連接 AFK 會取綜合等級與目的地最高等級中較低者。伺服器會在 AFK 開始時重新計算，不會信任前端預覽值；綜合等級本身沒有硬上限。

## How To Raise It | 如何提升

1. Raise the level of equipped upper and lower armor.
2. Install upgrade modules and raise their levels. Empty sockets count as level 0.
3. Equip both armor sides; a missing piece counts as level 0 and halves the average.

1. 提升已裝備上下身裝甲的等級。
2. 裝入升級模組並提升模組等級；空插槽以 Lv.0 計算。
3. 補齊兩件護甲；缺少其中一件會以 Lv.0 計入並拉低平均。
