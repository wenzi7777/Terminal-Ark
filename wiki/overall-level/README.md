# Overall Level | 綜合等級

Overall Level is a dynamic combat benchmark for your current team. It estimates which exploration levels your squad can clear smoothly with its present heroes, levels, rarity, and equipment.

綜合等級是根據你「目前隊伍」即時計算的戰力參考值，用來估計這支隊伍大致能穩定通過哪些探索等級。

---

## What Affects It | 影響因子

- Current team size. Empty or incomplete teams will score lower.
- Hero rarity, level growth, class growth, and all equipped gear.
- Equipped armor and modules, including gear count, rarity-derived stats, upgrade results, and combat affixes.
- Offensive and defensive combat stats such as HP, attack, defense, speed, critical chance, critical damage, cooldown recovery, extra turns, lifesteal, evasion, and guard.

- 當前隊伍的人數。隊伍為空或未成形時，綜合等級會明顯偏低。
- 英雄稀有度、等級成長、職業成長，以及實際穿戴的裝備。
- 上下防具與模組提供的數值，包括裝備數量、稀有度帶來的屬性、強化結果與 affix。
- 生命、攻防、速度、暴擊、暴傷、冷卻恢復、額外回合、吸血、閃避、格擋等實戰屬性。

## How It Is Calculated | 計算方式

The system snapshots your current team after equipment is applied, then compares it against exploration enemy benchmarks built from the live city map and enemy templates.

系統會先把你目前隊伍的最終戰鬥屬性快照下來，再拿去和目前城市地圖與敵人模板組出的探索基準敵群比較。

### Encounter Benchmark | 關卡基準

- Normal encounter: 2 standard enemies.
- Boss encounter: 1 boss plus 1.5 standard enemies as pressure weighting.
- Enemy rarity distribution follows the current exploration zone caps and rarity rules.

- 普通戰基準：2 隻一般敵人。
- Boss 戰基準：1 隻 Boss，加上 1.5 隻一般敵人的壓力權重。
- 敵人稀有度分布會遵守目前探索區域的星級上限與掉落規則。

### Win Ratio | 勝率指標

`winRatio = (teamEffectiveDps * teamEffectiveHp) / (enemyTotalDps * enemyTotalHp)`

- `teamEffectiveDps` combines each hero's real offensive stats and combat modifiers.
- `teamEffectiveHp` reflects armor, defenses, sustain, evasion, and guard.
- The highest exploration level that passes both the normal and boss thresholds becomes your Overall Level.

- `teamEffectiveDps` 會綜合英雄的實際輸出屬性與戰鬥修正。
- `teamEffectiveHp` 會反映護甲、防禦、續戰、閃避與格擋能力。
- 同時通過普通戰與 Boss 戰門檻的最高探索等級，就是你的綜合等級。

## What It Means In Practice | 實際意義

- Overall Level is a guidance value, not a guaranteed clear.
- Manual play, skill targeting, card synergy, mood, and temporary buffs can still change real outcomes.
- Changing team members or equipment updates the result immediately the next time profile data is loaded.

- 綜合等級是參考值，不是絕對保證通關。
- 實際操作、技能目標、卡牌連動、心情與暫時 Buff 仍會影響結果。
- 只要更換隊伍或裝備，下次重新載入個人資料時，綜合等級就會重新計算。

## How To Raise It | 如何提升

1. Use a full team instead of running with missing slots.
2. Raise hero levels and prioritize higher-rarity core members.
3. Finish equipment slots before chasing marginal upgrades.
4. Improve speed, survivability, and sustained damage instead of stacking only one attack stat.

1. 盡量讓隊伍滿編，不要空著位置。
2. 提高英雄等級，並優先培養高稀有度核心角色。
3. 先補齊裝備欄位，再追求邊際強化。
4. 不要只堆單一攻擊，速度、生存與續戰能力也會直接拉高綜合等級。
