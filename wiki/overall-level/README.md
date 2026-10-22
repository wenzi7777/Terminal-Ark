# Overall Level | 綜合等級

Overall Level is your account-wide equipment level. It drives neural-connection AFK rewards and is also your Signal Dive combat strength level: when a dive starts, it is converted into your combat power multiplier. It appears on the equipment screen, player profiles, Archive, and rankings.

綜合等級是帳號共用裝備的等級。它決定神經連接 AFK 的收益，同時也是訊號深潛的戰鬥強度等級：深潛開始時會換算成你的戰力倍率。顯示於裝備畫面、玩家資料、Archive 與排行榜。

## Combat Strength | 戰鬥強度

At the start of a Signal Dive, your Overall Level is frozen into a combat power multiplier that scales your card damage, block, affix protocol values, and maximum HP. Enemies scale with the dive's threat level on the same curve, so when your Overall Level keeps up with the threat, the difficulty stays roughly constant.

```text
power multiplier = 1.15 ^ ((max(16, Overall Level) − 16) / 16)
Lv.16 or below → ×1.00 · Lv.32 → ×1.15 · Lv.64 → ×1.52 · Lv.128 → ×2.66
```

深潛開始時，綜合等級會凍結成戰力倍率，放大卡牌傷害、護盾、詞綴協議數值與最大 HP。敵人依該場深潛的威脅等級走同一條曲線，所以綜合等級跟得上威脅時，難度大致不變。

```text
戰力倍率 = 1.15 ^ ((max(16, 綜合等級) − 16) / 16)
Lv.16 以下 → ×1.00 · Lv.32 → ×1.15 · Lv.64 → ×1.52 · Lv.128 → ×2.66
```

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
