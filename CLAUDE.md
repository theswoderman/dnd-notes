---
tags:
  - ignore
---
# CLAUDE.md

Working instructions for this Obsidian vault. Not a campaign note.

## What this vault is

D&D notes for two campaigns set in the same world, roughly a decade apart. Campaign 1 is concluded; Pilgrims of Panrelta is ongoing. The world, geography, and pantheon are shared — link into existing notes rather than duplicating them. Locations live under `Locations/`, not under a campaign folder, for this reason.

Each campaign has an index ([[00 - Campaign Index]], [[00 - Panrelta Index]]), a timeline, and a loose ends note. Nic did not play in Campaign 1; his Panrelta character is [[Thalrik Lastfeast]].

## Every edit

These rules apply to all note work, every time.

- **Encyclopedic voice.** Lead with what the subject IS, not the scene where the party learned about it.
- **Link every instance**, not just the first mention. Pipe when display text differs: `[[Thalrik Lastfeast|Thalrik]]`.
- **No em dashes.** Use a comma, colon, parentheses, or separate sentence.
- **American English.** Not colour/honour/travelled/centre/recognised/grey/armour.
- **Third person, no main character.** No "my character" on a character note. `index.md` is read by strangers — this applies hardest there.
- **Preserve uncertainty.** Keep guesses as guesses — "unconfirmed", "spelling unknown", "probably". Never silently promote a guess to fact.
- **Never invent campaign facts.** If something is unclear, record it as an open question and raise it.
- **Bold earns its place.** Key/value fields at the top of a note and the occasional thing that genuinely needs to stop the eye. Not emphasis several times a paragraph.
- **Don't say "nothing else is known."** End the passage where the information ends.
- **Don't restate what was just said.** No spelling out obvious deductions, restating with convoluted epithets, or adding summary lines that repeat the paragraph.
- **Raw session notes are archive.** Only add link syntax — never change wording. Quoted text stays exactly as spoken or written.

## Linking

**Do not link inside:** frontmatter, code spans and file paths, headings, blockquotes, a note's own "Also known as" line, or chat speaker labels in session notes.

## Note conventions

YAML frontmatter, `#` H1 matching the filename, bold key/value lines, then sections.

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

## Sessions
- [[Session N]]
```

Locations use `**Region:**` and `**Disposition:**`. Events use `**When:**`, `**Part of:**`, `**Sessions:**`, then `## What happened`.

Common tags: `character, location, event, faction, item, deity, lore` plus qualifiers (`party, villain, ally, major, deceased, panrelta, crossover`). Tag Panrelta notes `panrelta` so the two campaigns can be filtered apart.

Give characters short-name aliases so informal session notes link cleanly.

Character notes carry a `**Player:**` line linking to the player note in `Players/`, as the first field. **[[Loryn Malcovitch]] is [[Nick]]'s character, not Nic's** — the names are one letter apart and this has been gotten wrong before.

## Voice details

The "every edit" checklist covers the core rules. These expand on them.

**Encyclopedic voice, not narrative of discovery:**
Bad: "Named by The Collector as he woke, furious that The Good Ones had cured his lycanthropy: the Black Blood Pack would come for them."
Good: "A lycanthrope pack in the service of Malar. The Collector presumably belonged to it, and warned that the pack would come for The Good Ones in the moments before his death."

Plain, direct prose. Contractions fine. Vary sentence length.

**No main character exception:** the early Panrelta record is missing because Thalrik joined partway through. That is worth explaining where the recorded order needs it.

**Open questions live only in the campaign's loose ends note** ([[Panrelta Loose Ends]] or [[Campaign 1 Loose Ends]]), not scattered through individual notes. Entity notes state what's known and stop. Point to the loose ends note: "See [[Panrelta Loose Ends]] for open questions."

## Source authority

**Nic's account wins** over other sources when they conflict. [[Grant]]'s [[Prelude for Thalrik Lastfeast]] spells some names differently; the vault spellings are canonical, with losing spellings kept as aliases.

**The map wins on place names.** `Map of Estrana.webp` on [[Estrana]] is authoritative.

**Campaign 1 notes are frozen.** Reed is writing a summary of the final three levels. Until it arrives, Campaign 1 notes reflect a mid-campaign state — do not "fix" them by inference. When it arrives: create event notes, update [[Campaign 1 Timeline]], [[Queensbane]], [[00 - Campaign Index]], and work through [[Campaign 1 Loose Ends]].

---

## Workflows

Everything below applies only when a specific workflow is triggered.

### Session note processing

Raw notes arrive in `Session Notes/<campaign>/`. When asked to process one:

1. Read it. Identify new entities versus updates to existing notes.
2. Create new notes; update existing ones in place.
3. Add `## Sessions` backlinks on every note touched.
4. Update the timeline and the campaign's loose ends note.
5. Update the campaign index if the event list or cast changed.
6. Update `index.md` — **Where things stand**, chronology, recorded-events list.
7. Run the verification script.

Verify archive integrity: strip links from the raw note before and after, assert text is identical.

### Update runs

"Run an update" means the full sweep, not just one file.

**1. Read the suggestion box.** `Suggestions/Suggestion Box.md`. Text below the divider is unprocessed. Treat each entry as its own suggestion.

**2. Find what else changed.** Diff git from the date of the newest `Suggestions/Suggestion History/` note. Ignore `.obsidian/` churn. If Nic renamed files, sweep for stale prose mentions.

**3. Incorporate each suggestion.** Three outcomes:
- **New information** — add to every note where it belongs.
- **Already covered** — change nothing, record where it lived.
- **Conflicts with canon or invents a fact** — stop and ask Nic. Collect all questionable suggestions and raise them together.

**4. Write a history entry.** One note per day (`YYYY-MM-DD.md`) in `Suggestions/Suggestion History/`, tagged `ignore` and `suggestion`. Each suggestion is an H2 with verbatim quote, **Status**, and H3 subsections for **Incorporated into**, **Already covered**, **Notes**. No attribution field. Then clear processed text from the box, leaving header and divider.

**5. Refresh `index.md`.**

### Corrections in chat

Corrections Nic gives in conversation are canon immediately. Every one gets a history entry same as box entries — an H2 in that day's `Suggestions/Suggestion History/` note with verbatim quote and links to notes touched.

The unit is the message: one message with three corrections = one entry. Style and process changes count when they rewrite notes. Entries backfilled from transcripts say so in **Notes**.

### Verification

Run after any batch of edits. Checks broken links, YAML errors, duplicate filenames.

```bash
python3 -c "
import re,glob,os,collections,yaml
files=[p for p in glob.glob('**/*.md',recursive=True) if not p.startswith('.obsidian')]
strip=lambda t: re.sub(r'```.*?```','',t,flags=re.S)
names={}; dupes=collections.defaultdict(list)
for a in glob.glob('**/*',recursive=True):
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

**Assert on find-and-replace.** Use `assert old in s` before replacing — a silent no-op has caused missed edits before.

---

## Guardrails

### Git and publishing

The vault is published via GitHub (`theswoderman/dnd-notes`, branch `main`) and rendered by Flowershow. Everything written here is public.

**`index.md` is the homepage** — a maintenance target on every session and update run. Keep the note count approximate.

**Git is read-only by default.** Use `git log` and `git diff` freely. Nic's backup plugin commits and pushes automatically — check `git fetch` and compare before assuming anything needs publishing.

**Commit or push only when Nic says so in that session.** Never `checkout`, `reset`, `rebase`, or anything that rewrites history. Commit as Nic (`git -c user.name=... -c user.email=...`), leave `.obsidian/` out.

**`git mv` fails in the sandbox** — use plain `mv`. If a `.git/index.lock` appears, delete it.

**Case-insensitive repo.** Renaming to fix only capitalization requires two moves via a temporary name.

### Do not touch

- `.obsidian/` — exception: graph color groups on request, with Obsidian closed
- `cssclass: timeline` on [[The Demon War]]
- `ddb:` frontmatter (D&D Beyond links)
- `Templates/` — update content if conventions change, but don't rename or move files
- `Suggestions/Suggestion Box.md` header and divider — only clear text below the divider
- `Suggestions/Suggestion History/` — append-only, never edit or delete
- After Nic renames files: Obsidian fixes wikilinks but not prose mentions — sweep for those

`Area:` and `Favorability:` are not plugin-wired. When converting old notes, fold into body as `**Region:**` and `**Disposition:**`.
