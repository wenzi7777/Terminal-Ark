# Overall Level | 綜合等級

Overall Level is a dynamic combat benchmark for your current team. It estimates which exploration levels your squad can clear smoothly with its present heroes, levels, rarity, and equipment.

綜合等級是根據你「目前隊伍」即時計算的戰力參考值，用來估計這支隊伍大致能穩定通過哪些探索等級。

---

## What Affects It | 影響因子

- Only your 5 strongest heroes (by combat score) count toward the result. The rest of your roster does not affect it.
- Those 5 are then score-normalized to a historical 3-hero baseline so a full TD deploy does not inflate the number with N² scaling.
- Hero rarity, level growth, class growth, and all equipped gear.
- Equipped armor and modules, including gear count, rarity-derived stats, upgrade results, and combat affixes.
- Offensive and defensive combat stats such as HP, attack, defense, critical chance, critical damage, lifesteal, evasion, and guard. (Attack interval / legacy speed is not a separate overall-level stat after the TD rework.)

- 只有戰力最高的 5 隻英雄會參與計算，其餘替補英雄不影響這個數字。
- 這 5 隻會再依歷史 3 人基準做勝率正規化，避免滿編 TD 部署因 N² 公式把綜合等級灌爆。
- 英雄稀有度、等級成長、職業成長，以及實際穿戴的裝備。
- 上下防具與模組提供的數值，包括裝備數量、稀有度帶來的屬性、強化結果與 affix。
- 生命、攻防、暴擊、暴傷、吸血、閃避、格擋等實戰屬性。（TD 改版後，攻速／舊速度屬性不再單獨進綜合等級。）

## How It Is Calculated | 計算方式

The system snapshots your current team after equipment is applied, then compares it against exploration enemy benchmarks built from the live city map and enemy templates (including TD ecology enemies that use `rank` + `td.basicAttack`, not legacy `enemyType` / `isBoss` only).

系統會先把你目前隊伍的最終戰鬥屬性快照下來，再拿去和目前城市地圖與敵人模板組出的探索基準敵群比較（已支援 TD 生態模板的 `rank` 與 `td.basicAttack`）。

### Encounter Benchmark | 關卡基準

- Normal encounter: 4 standard (non-boss) enemies — regular **and elite** templates, weighted by exploration rarity rules.
- Boss encounter: 1 boss (`rank === 'boss'` or legacy `isBoss`) plus 4 standard enemies as pressure.
- Boss level is slightly above the current exploration level (clamped to the area max).

- 普通戰基準：4 隻非 Boss 敵人（**含 regular 與 elite**），稀有度依探索區域規則加權。
- Boss 戰基準：1 隻 Boss（`rank === 'boss'` 或舊欄位 `isBoss`）+ 4 隻一般敵人壓力。
- Boss 等級略高於當前探索等級（不超過該區域上限）。

### Win Ratio | 勝率指標

`winRatio = (teamEffectiveDps * teamEffectiveHp) / (enemyTotalDps * enemyTotalHp)`

then normalized by squad size:

`winRatio *= (3 / N)²` where N is the number of heroes in the overall-level squad (up to 5).

- `teamEffectiveDps` combines each hero's real offensive stats and combat modifiers.
- `teamEffectiveHp` reflects armor, defenses, sustain, evasion, and guard.
- The highest exploration level that passes both the normal (≥ 1.3) and boss (≥ 1.2) thresholds becomes your Overall Level.

- `teamEffectiveDps` 會綜合英雄的實際輸出屬性與戰鬥修正。
- `teamEffectiveHp` 會反映護甲、防禦、續戰、閃避與格擋能力。
- 同時通過普通戰（≥ 1.3）與 Boss 戰（≥ 1.2）門檻的最高探索等級，就是你的綜合等級。

## What It Means In Practice | 實際意義

- Overall Level is a guidance value, not a guaranteed clear.
- Manual play, skill targeting, TD positioning, and temporary buffs can still change real outcomes.
- Changing team members or equipment updates the result the next time profile / team data is loaded.

- 綜合等級是參考值，不是絕對保證通關。
- 實際操作、技能目標、TD 站位與暫時 Buff 仍會影響結果。
- 只要更換隊伍或裝備，下次重新載入個人資料／隊伍資料時，綜合等級就會重新計算。

## How To Raise It | 如何提升

1. Focus on your 5 strongest core heroes — level, gear, and upgrade them first. The other roster slots don't affect Overall Level.
2. Raise hero levels and prioritize higher-rarity core members.
3. Finish equipment slots before chasing marginal upgrades.
4. Improve survivability and sustained damage instead of stacking only one attack stat.

1. 優先把戰力最高的 5 隻核心英雄練起來、裝備齊全，其餘替補位置不影響綜合等級。
2. 提高英雄等級，並優先培養高稀有度核心角色。
3. 先補齊裝備欄位，再追求邊際強化。
4. 不要只堆單一攻擊，生存與續戰能力也會直接拉高綜合等級。
