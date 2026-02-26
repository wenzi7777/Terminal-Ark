# Terminal Ark Changelog

## APP BUNDLE VERSION v0.5.0 Public Beta
## SERVER BUNDLE VERSION v0.5.0 Public Beta

## Release Date: Feb. 26th 2026 15:30 JST

### Bug Fixes
- Fixed a race condition in multiplayer dungeons where non-leader members could miss real-time vote updates due to delayed subscription initialization.
- Added a loading animation to the confirm button in the DataVault overlay to prevent accidental duplicate submissions during Cache and Memory operations.
- Resolved an intermittent battle issue that triggered the error: “Cannot read properties of undefined (reading 'reduce').”
- Fixed a bug where fleeing a battle with surviving heroes incorrectly redirected players to the hospital screen.

### New Features
- Displayed a “Player is thinking…” overlay to teammates when a player selects a card during multiplayer dungeon battles.
- Added a full-screen loading screen during app initialization to improve startup experience.
- Introduced a new “Gacha History” feature for reviewing past draws.

### Improvements
- Added an “Apply Balance Adjustment” option to 1-1 Discovery Dungeon, allowing new players to clear it smoothly with the default team setup.
- Reworked the new player tutorial for improved onboarding flow and clarity.
- Added empty-state indicators for Heroes and Items on /disc/heroes and /disc/inventory pages.

### Others
- Included various minor fixes and performance optimizations.

***This is a hotfix update and will be installed automatically. You will receive a notification prompting you to refresh the page after the hotfix is installed.***