# Network Maintenance Rules | 網路維護規則

This page explains how player networks consume resources during maintenance, what happens if maintenance fails, and how to prepare.

## Maintenance Cycle | 維護週期
- Each network has a `next_maintenance_at`. When the time arrives, the maintenance job checks resources.
- The first maintenance after creation is free (no resource cost).
- After the first cycle, maintenance occurs every 7 days by default.

## Costs | 維護成本
- Memory cost: `Level * 100` KiB.
- DDoS Protection cost: `Level * 50` KiB.
- Costs are deducted only when maintenance succeeds.

## Success & Failure | 成功與失敗
- If Memory and DDoS Protection are both sufficient, resources are deducted and `next_maintenance_at` advances by 7 days.
- If either resource is insufficient, the network is dissolved:
  - The network record is deleted.
  - Members are removed from the network.
  - Members’ `userNetworkId` and support hero assignments are cleared; heroes return to their inventory.

## Preparation Tips | 準備建議
- Keep a buffer above the required Memory and DDoS Protection to avoid dissolution.
- Monitor remaining time and costs on the network overview page.
- Assign members to contribute resources early if you’re close to the threshold.
