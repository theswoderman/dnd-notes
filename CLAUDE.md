---
tags:
  - ignore
---
# CLAUDE.md

Working instructions for this Obsidian vault. Not a campaign note — tagged `ignore` so it stays out of the graph.

## What this vault is

D&D notes for **two campaigns set in the same world**, roughly a decade apart.

| | Campaign 1 | Pilgrims of Panrelta |
|---|---|---|
| Party | [[The Sons of Thunder]] | [[The Good Ones]] |
| Nic's character | [[Loryn Malcovitch]] (former) | [[Thalrik Lastfeast]] |
| Status | Concluded at level 20 | Ongoing, ~session 28 |
| Index | [[00 - Campaign Index]] | [[00 - Panrelta Index]] |
| Timeline | [[Timeline]] | [[Panrelta Timeline]] |

**Panrelta is set ten years after Campaign 1 ends.** The Sons of Thunder are alive and famous. Confirmed crossovers: [[Thol]] is [[Bathoz Manefell]]'s adopted son; [[Yosco]] appears in both; [[The Good Ones]] met [[Jäkel Aleister le Rouge|Jakel]] at a dinner in [[Stonehold]]; [[The Abyssal Orb]] is bound for the Sons of Thunder. Geography and pantheon are shared — link into existing notes rather than duplicating them.

## Folder layout

```
Deities/
Events/Campaign 1/Events/
Events/Pilgrims of Panrelta/Events/
Groups/
Items and Artifacts/
Locations/Material Plane/
Locations/Planes and Extraplanar/
Lore/                     timelines and world lore
People/NPCs/              + Antagonists/, Campaign 1 Allies/, Campaign 1 Notable NPCs/
People/The Good Ones/     Panrelta party
People/The Sons of Thunder/
Session Notes/<campaign>/ raw session notes, archival
Templates/
```

Locations live under `Locations/`, not under a campaign folder, because the world is shared.

## Note conventions

Campaign 1 style is the standard for everything. YAML frontmatter, `#` H1 matching the filename, bold key/value lines, then sections.

```markdown
---
tags: [character, party, panrelta, dwarf]
aliases: [ShortName]
---
# Full Name

**Race:** ...
**Affiliation:** [[Group]]
**Status:** Alive

## Summary
Prose.

## Key moments
- Bullet — see [[Event Note]]

## Connections
- [[Someone]] — relationship

## Sessions
- [[Session N]]
```

Locations use `**Region:**` and `**Disposition:**`. Events use `**When:**`, `**Part of:**`, `**Sessions:**`, then `## What happened`.

Common tags: `character, location, event, faction, item, deity, lore` plus qualifiers (`party, villain, ally, major, deceased, panrelta, crossover`). Tag Panrelta notes `panrelta` so the two campaigns can be filtered apart.

Give characters **short-name aliases** (`Thalrik`, `Gribnik`, `Jakel`) so informal session notes link cleanly.

## Rules

**Link every instance**, not just the first mention. Do not link inside: frontmatter, code spans and file paths, headings, blockquotes, a note's own "Also known as" line, or chat speaker labels in session notes. Pipe when the display text differs: `[[Thalrik Lastfeast|Thalrik]]`.

**American English.** Not colour/honour/travelled/centre/recognised/grey/armour.

**Preserve uncertainty.** Nic's notes contain guesses. Keep them as guesses — "unconfirmed", "spelling unknown", "probably". Never silently promote a guess to fact or normalize a name he flagged as uncertain.

**Never invent campaign facts.** If something is unclear, record it as an open question and raise it.

## Session note workflow

Raw notes arrive in `Session Notes/<campaign>/`, named `Session N`. When asked to process one:

1. Read it. Identify what's new versus what updates an existing note.
2. Create new notes for new entities; update existing ones in place.
3. Add `## Sessions` backlinks on every note touched.
4. Add a row to the **session log** table in the campaign timeline listing what was created and updated.
5. Update the timeline's event list and **loose threads**.
6. Update the campaign index if the event list or cast changed.
7. Run the verification script below.

**Raw session notes are an archive.** Only ever *add link syntax* to them — never change wording. Verify by stripping links from both versions and asserting the text is identical.

## Verification

Run after any batch of edits. Checks broken links, YAML errors, and duplicate filenames.

```bash
cd "/sessions/<session>/mnt/dnd notes" && python3 -c "
import re,glob,os,collections,yaml
files=[p for p in glob.glob('**/*.md',recursive=True) if not p.startswith('.obsidian')]
strip=lambda t: re.sub(r'```.*?```','',t,flags=re.S)   # ignore code fences
names={}; dupes=collections.defaultdict(list)
for a in glob.glob('**/*',recursive=True):             # attachments are valid link targets
    if os.path.isfile(a) and not a.endswith('.md') and not a.startswith('.obsidian'):
        names[os.path.basename(a).lower()]=a
for p in files:
    b=os.path.splitext(os.path.basename(p))[0]; dupes[b.lower()].append(p); names[b.lower()]=p
    m=re.match(r'^---\n(.*?)\n---',open(p,encoding='utf-8').read(),re.S)
    if m:
        try: fm=yaml.safe_load(m.group(1)) or {}
        except: print('YAML ERROR',p); continue
        al=fm.get('aliases') or []
        if isinstance(al,str): al=[al]
        for a in al:
            if a: names.setdefault(str(a).lower(),p)
b=collections.Counter(t for p in files for l in re.findall(r'\[\[([^\]]+)\]\]',strip(open(p,encoding='utf-8').read())) for t in [l.split('|')[0].split('#')[0].strip().replace(chr(92),'')] if t.lower() not in names)
print('notes:',len(files),'| broken:',sum(b.values()),dict(b))
print('dupes:',{k:v for k,v in dupes.items() if len(v)>1})
"
```

**Assert on find-and-replace.** A silent no-op has bitten before: a chronology rewrite failed to apply because an earlier auto-linking pass had changed the text, while other edits in the same script succeeded. Use `assert old in s` before replacing.

## Do not touch

- `.obsidian/` — plugin config. Breadcrumbs uses `up/down/same/next/prev`; `types.json` registers the recognized frontmatter fields. Exception: graph color groups in `graph.json` and `plugins/extended-graph/data.json` are managed on request. **Obsidian must be closed when writing these** — it flushes in-memory state over the file on quit and silently discards the edit.
- `cssclass: timeline` on [[The Demon War]] and [[The Great War]] — used by a theme.
- `ddb:` frontmatter — D&D Beyond character links.
- `Templates/` — Person, Location, Group, Event. These match the conventions above and are wired to both the core Templates plugin and Templater, where Nic has hotkeys bound to them. **If a convention changes, update these too**, and don't rename or move the files or the hotkeys break.
- Nic reorganizes and renames files himself. After a rename, Obsidian fixes wikilinks but **not plain-text prose mentions** — sweep for those.

`Area:` and `Favorability:` are *not* wired to any plugin. When converting old notes, fold them into the body as `**Region:**` and `**Disposition:**` rather than dropping the data.

## Name discrepancies — settled

Grant's [[Prelude for Thalrik Lastfeast]] spells several names differently from the vault. Nic has ruled on all of them. **Canonical forms:**

[[Aeralath]] · **[[Golden Plains|The Golden Plains]]** · [[Magus Trollbeater]] · [[Loryn Malcovitch|Malcovitch]] · [[Whisperwood]] · [[Kelara]] · [[Ishtir Marsh|Ishtir]] · [[Blackwaste]]

The vault spelling won everywhere except **Golden Plains**, which was renamed from "Golden Planes" to match the prelude. Each losing spelling is kept as an alias so older links still resolve — do not "fix" them by renaming.

When Grant's wording conflicts with Nic's own account, **Nic's account wins.** The bulette night in [[Thalrik's Road to Stonehold]] is the worked example.

**The map wins on place names.** `Map of Estrana.webp`, embedded on [[Estrana]], is authoritative for the spelling of locations. **[[Silnothas]]** was renamed from "Silnothis" to match it, with the old spelling kept as an alias — same pattern as Golden Plains. Places drawn on the map with no note simply have not come up in play; that is expected and not a gap to fill.

## Open questions

- "shae de claw" and "zogmoi" — spellings unknown, from the elder-entity mention in session 28
- "yorrisk upon the dawning" — [[The Dawning]] is confirmed as the celebration of [[Aeralath]]'s defeat and the tenth is approaching, so this reads as a deadline. "Yorrisk" is still unidentified
- Name of the arcane college [[Davynn Brindleknot|Davynn]] founded in the [[Blackwaste]] — the prelude marks it TBD
- Whether [[The Maiden]]'s 10,000 gold was paid or the apex griffon heart delivered
- Whether [[The Collector]] works for [[The Maiden]] — the centaur hooves suggest yes
- [[Beemo]], [[Falstad Firebeard]] and [[Gegga]] previously shared one `ddb:` URL; Nic has since corrected these
- **The year.** [[Estrana]] records the current year as 1016 A.P.; `Map of Estrana.webp` is dated 1017 A.P. Nic's read is that 1016 was the year Campaign 1 *started* — he is checking with that campaign's DM. Do not change the [[Estrana]] note until he confirms

## Pending work

Nic plans to supply a campaign summary covering **the final three levels of Campaign 1**. When it arrives: create event notes in `Events/Campaign 1/Events/`, file new people and places into existing folders, and update [[Timeline]], [[Queensbane]] (the six-plane attunement checklist), and [[00 - Campaign Index]]. Check each of the loose threads on [[Timeline]] and mark which the ending resolves. [[The Sons of Thunder]] still carries a stale "Current objective" section that the summary should replace.
