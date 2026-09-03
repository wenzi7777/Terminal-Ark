# Overall Level | 綜合等級

Overall Level estimates the deepest Signal Dive threat level (`threatLevel`) your account can currently clear reliably, based on your active team profile's support commands and your account-wide equipment.

綜合等級估算的是：以你目前出戰 Profile 的技能陣容與帳號裝備，大概能穩定通過訊號深潛（Signal Dive）的哪個威脅等級（`threatLevel`）。

---

## What Affects It | 影響因子

- The **3 heroes in your currently active team profile** — not your whole roster. Each contributes its Rank-derived power level; switching profiles or hero ranks changes the result immediately.
- Your **account-wide equipment** (`playerEquipment`): the single upper/lower armor loadout and its socketed modules. Equipment is shared across the whole account, not equipped per hero.
- There is no upper bound. As your gear and hero ranks grow, Overall Level keeps climbing — it does not cap at a fixed number.

- **目前出戰 Profile 的 3 位英雄**——不是整個收藏庫。每位英雄依 Rank 換算出的等級都會影響結果；切換 Profile 或提升 Rank 會立刻改變數值。
- **帳號共用裝備**（`playerEquipment`）：全帳號只有一套上/下裝甲與插槽模組，不是每個英雄各自穿裝。
- 沒有上限。裝備與英雄 Rank 持續成長，綜合等級也會持續往上，不會卡在固定數字。

## How It Is Calculated | 計算方式

Overall Level is a fast estimate, not a literal simulation of a Signal Dive run. It combines two power scales onto the same exponential curve the game already uses to scale Signal Dive difficulty (`sharedLevelScale(level) = 1.15^(level/16)`), then solves for the `threatLevel` at which that combined power would land:

綜合等級是快速估算值，不是真的跑一次訊號深潛模擬。它把兩塊戰力換算到遊戲本身縮放訊號深潛難度時用的同一條指數曲線上（`sharedLevelScale(level) = 1.15^(level/16)`），再反推出對應的 `threatLevel`：

- **Hero command power** — the average Rank-derived level (1–60) of the 3 active heroes, converted to a scale via `sharedLevelScale`.
- **Equipment power** — the account's equipped armor/module bonuses (`outputPermille`, `integrityPermille`), converted to an offense/survivability multiplier.
- Both multiplied together and solved back into a `threatLevel` estimate.

- **英雄技能陣容戰力**——出戰 3 位英雄依 Rank 換算等級（1–60）取平均，套進 `sharedLevelScale`。
- **裝備戰力**——帳號裝備／模組加成（`outputPermille`、`integrityPermille`），換算成攻防倍率。
- 兩者相乘後反推回對應的 `threatLevel` 估計值。

Implementation: `backend/supabase/functions/_shared/overall_level.ts`. Its calibration constant is anchored to `_shared/signal_dive/balance_sim.ts`'s Monte Carlo verification (a legendary-quality, optimized-play loadout at gear level == `threatLevel` clears ~80–90%) — see the comment block at the top of `overall_level.ts` for the full derivation, and `_shared/signal_dive/overall_level_calibration_test.ts` for the dev-only tool used to re-check it.

實作位置：`backend/supabase/functions/_shared/overall_level.ts`。校準常數的基準是 `_shared/signal_dive/balance_sim.ts` 的 Monte Carlo 驗證結果（legendary 品質、optimized 打法、裝等 == `threatLevel` 時通關率約 80–90%）——完整推導見 `overall_level.ts` 檔頭註解，重新校準用的 dev-only 工具在 `_shared/signal_dive/overall_level_calibration_test.ts`。

## What It Means In Practice | 實際意義

- Overall Level is a guidance value, not a guaranteed clear.
- The estimate does not yet model support-command effects during a run — `balance_sim.ts`'s own clear-rate verification runs with an empty support-command loadout, so the hero-power dimension is a design extrapolation pending future calibration once support commands are modeled in the simulator.
- Manual play, card draws, and run RNG still change real outcomes.
- Changing your active profile's heroes or your equipped gear updates the result the next time profile / team data is loaded.

- 綜合等級是參考值，不是絕對保證通關。
- 目前的估算還沒有把「戰鬥中實際觸發技能陣容」的效果模擬進去——`balance_sim.ts` 本身的通關率驗證是在技能陣容留空的情況下跑的，所以英雄戰力這塊是設計外推值，等模擬器支援技能陣容後需要重新校準。
- 實際操作、抽牌與對局隨機性仍會影響結果。
- 只要更換出戰 Profile 的英雄或帳號裝備，下次重新載入個人資料／隊伍資料時，綜合等級就會重新計算。

## How To Raise It | 如何提升

1. Rank up the 3 heroes in your active team profile — other roster slots don't affect Overall Level.
2. Upgrade your account's equipped armor level, rarity, and quality; fill both armor slots and their module sockets.
3. Switching to a profile with higher-Rank heroes raises Overall Level immediately, even without new gear.

1. 提升出戰 Profile 3 位英雄的 Rank——其他替補位置不影響綜合等級。
2. 提升帳號裝備的裝等、稀有度與品質；補齊兩個裝甲欄位與模組插槽。
3. 切換到 Rank 更高的英雄組成的 Profile，即使沒有新裝備也會立刻拉高綜合等級。
