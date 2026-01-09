# Equipment Names

This folder stores equipment name pools for community contributions.

## File Format
One JSON per language, named by language code (e.g. `zh_tw.json`).

Required keys:
- `rarityPrefixes`
- `affixWordB`
- `affixWordC`
- `slotSuffixes`

Optional keys:
- `language-name`

## Notes
- All language files must share the same key set.
- Array order affects name composition. Keep existing order unless you have a clear reason to change it.
