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
| Nic's character | — did not play | [[Thalrik Lastfeast]] |
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
Suggestions/              shared Suggestion Box.md + Suggestion History/
People/NPCs/              + Antagonists/, Campaign 1 Allies/, Campaign 1 Notable NPCs/
People/The Good Ones/     Panrelta party
People/The Sons of Thunder/
Players/                  the real people at the table, tagged ignore
Session Notes/<campaign>/ raw session notes, archival
Templates/
Events/Totally safe boat trip one shot/   one-shot, outside both campaigns
People/Totally safe boat trip one shot/   the one-shot party
```

Locations live under `Locations/`, not under a campaign folder, because the world is shared.

The vault is framed around two campaigns, but play outside them gets its own `Events/` subfolder.

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

## House voice

Plain, direct prose. Contractions are fine. Vary sentence length. Prefer a full sentence to a fragment where it reads better.

**No em dashes.** Use a comma, a colon, parentheses, or a separate sentence.

**Bold and headings have to earn their place.** The older notes lean on bold for emphasis several times a paragraph; that is the habit being moved away from. Keep bold for the key/value fields at the top of a note and for the occasional thing that genuinely needs to stop the eye.

**Scope: notes created or rewritten from now on.** Existing notes stay in the older style until they are rewritten for some other reason. Do not sweep the vault for em dashes. [[Panrelta Timeline]] is the worked example of the new voice; `index.md` and everything else are still in the old one on purpose, not by neglect.

Two things this never applies to. Raw session notes in `Session Notes/` are archive and only ever gain link syntax. Quoted text stays exactly as it was said or written, which covers the suggestion quotes in `Suggestions/Suggestion History/`, in-world quotes, and [[Grant]]'s prelude.

## Player notes

`Players/` holds one note per real person at the table — [[Nic]], [[Nick]], [[Reed]], [[Grant]], [[Ian]], [[Cameron]], [[Tyler]] — each tagged `ignore` and `player`, each with a table of the characters that person has played and which campaign each belongs to. `ignore` keeps real people out of the graph, matching this file and the suggestion history; the wikilinks still work.

Character notes carry a `**Player:**` line linking to the player note, as the first field. Prose that names a player links too — "[[Grant]]'s old character", "[[Ian]] was not playing that night".

**Two deliberate exceptions.** Chat speaker labels in session notes stay unlinked, per the linking rules above. And this file stays unlinked: it names Nic constantly as the person giving instructions, not as a player.

There is no Player template in `Templates/`; the seven notes were written by hand and are the pattern.

**[[Loryn Malcovitch]] is [[Nick]]'s character, not Nic's.** The two names are one letter apart and this has been gotten wrong before. Nic did not play in Campaign 1 at all.

## The published site

The vault is a git repo published to GitHub at `theswoderman/dnd-notes` (branch `main`) and rendered as a site by Flowershow. Three consequences:

**`index.md` at the vault root is the homepage.** Tagged `ignore`, `index`, `moc` — a reader-facing overview, not a campaign note, deliberately outside the graph. It restates the campaign table, the chronology from [[The Sundering]] to the current session, a **Where things stand** section, and a note count. All of that drifts the moment notes change, so it is a maintenance target on every session and every update run. Treat the note count as approximate — round it rather than chasing exactness.

**Anything written here is public.** Names, open questions and half-guesses are all visible. This doesn't change the rules below, but it raises the cost of a bad guess.

**Git is read-only by default.** Use `git log` and `git diff` freely. Nic's backup plugin already commits *and* pushes on its own, so vault edits reach the site without any help — check `git fetch` and compare `origin/main...main` before assuming anything needs publishing.

**Commit or push only when Nic says so in that session.** Standing permission is not implied by a past yes. Even then, never `checkout`, `reset`, `rebase`, or anything else that rewrites history or discards working state. Commit as Nic (`git -c user.name=... -c user.email=...`) rather than writing a git identity into the repo config, and leave `.obsidian/` churn out of the commit — the backup plugin handles it.

**`git mv` fails in the sandbox** — it cannot take `.git/index.lock` and leaves a stale lock behind, which then blocks the backup plugin from committing at all, silently. Use plain `mv`, and if a lock appears, delete `.git/index.lock`.

**The repo is case-insensitive** (`core.ignorecase` is true, on a Windows-backed filesystem). Renaming a file or folder to fix only its capitalization changes nothing as far as git is concerned, so the old casing stays in the published URLs. Forcing it through takes two moves via a temporary name.

## Rules

**Link every instance**, not just the first mention. Do not link inside: frontmatter, code spans and file paths, headings, blockquotes, a note's own "Also known as" line, or chat speaker labels in session notes. Pipe when the display text differs: `[[Thalrik Lastfeast|Thalrik]]`.

**American English.** Not colour/honour/travelled/centre/recognised/grey/armour.

**No main character.** Notes are written in the third person, about the world and the parties, not from Nic's point of view. No "my character" on a character note, and no cross-links between characters that exist only because the same person played both; the `**Player:**` field and the `Players/` notes carry that already. This applies hardest to `index.md`, which strangers read. **One exception:** the early Panrelta record is missing because [[Thalrik Lastfeast]] joined the campaign partway through, and that is worth explaining wherever the recorded order needs it.

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
7. Update `index.md` — **Where things stand**, the chronology, and the recorded-events list if the session added one.
8. Run the verification script below.

**Raw session notes are an archive.** Only ever *add link syntax* to them — never change wording. Verify by stripping links from both versions and asserting the text is identical.

## Update runs

"Run an update" or "update the wiki" means the full sweep below, not just one file. Do all five steps in order.

**1. Read the suggestion box.** `Suggestions/Suggestion Box.md`. Any text *below the divider line* is unprocessed player input. The file is shared — other players edit it directly, so expect informal, misspelled, or partial entries, and expect several unrelated suggestions at once. Treat each as its own suggestion.

**2. Find what else changed.** The vault is a git repo with automatic `vault backup: <timestamp>` commits, so git is the source of truth for "since last time." Get the date of the newest note in `Suggestions/Suggestion History/`, then diff from the commit at that point:

```bash
cd "/sessions/<session>/mnt/dnd notes"
git log --oneline --since="<date of last suggestion history note>" -- . ':(exclude).obsidian'
git diff --stat "HEAD@{<date>}" HEAD -- . ':(exclude).obsidian'
```

Ignore `.obsidian/` churn entirely — plugin files rewrite themselves constantly and mean nothing. If Nic renamed or moved files, sweep for stale plain-text prose mentions (see Do not touch). If he added notes by hand, check they follow the conventions above and are linked from the relevant index and timeline.

**3. Incorporate each suggestion.** Cross-reference against what already exists before writing anything. Three outcomes:

- **New information** — add it to every note where it belongs, not just the most obvious one. A suggestion about a character usually also touches their group, their location, and the relevant event note.
- **Already covered** — change nothing. Record where the information already lived.
- **Conflicts with canon, or invents a fact** — **stop and ask Nic.** Do not apply it and do not guess. Player suggestions are not canon; the `Never invent campaign facts` and `Preserve uncertainty` rules outrank a suggestion. Collect all questionable suggestions and raise them together at the start of the run rather than one at a time.

**4. Write a history note.** One note per suggestion in `Suggestions/Suggestion History/`, from `Templates/Suggestion.md`. Filename `YYYY-MM-DD - Short description`, so the folder sorts chronologically. It records the suggestion verbatim (quote it, typos and all — it is a record of what was said), the date received, and wikilinks to every note touched. **No attribution field** — the box arrives via Nic, so who submitted it is not recoverable and not worth guessing at. If nothing was touched because the information already existed, link to where it lives instead. Then **clear the processed text from the box**, leaving the header and divider so it is an empty inbox again.

History notes are tagged `ignore` **and** `suggestion` — `ignore` keeps them out of the graph, matching this file. They still use real wikilinks, so the links stay clickable; they just do not draw graph edges. Do **not** add attribution lines to the campaign notes themselves — the history note's links are the audit trail, and the notes stay clean.

**5. Refresh `index.md`.** Same targets as the session workflow — **Where things stand**, the chronology, the note count. If the run only touched a character detail this may be a no-op; check rather than assume.

Run the verification script when the whole sweep is done.

## Corrections given in chat

Nic corrects things in conversation as often as through the box, and those corrections are canon the moment he gives them. **Every one gets a history note, same as a box entry.** Write it in `Suggestions/Suggestion History/` from `Templates/Suggestion.md`, quote him verbatim, and link every note touched. Do this in the same session, not at the next update run.

**The unit is the message, not the fact.** One message carrying three unrelated corrections gets one entry, with the three listed under **Incorporated into**. Splitting them produces noise and loses the context they arrived in.

Style and process changes count too, not just campaign facts, when they rewrite a note wholesale. [[2026-08-12 - Rewrite the Panrelta Timeline in a plainer style]] is the worked example.

Everything else is unchanged: tagged `ignore` and `suggestion`, no attribution line, never edited after the fact. A correction that reverses an earlier one gets a new entry pointing at the old.

Entries backfilled from chat transcripts say so in **Notes**, since what was touched is reconstructed rather than observed. The `mcp__session_info__` tools can read past session transcripts, which is where a backfill gets its verbatim quotes.

## Verification

Run after any batch of edits. Checks broken links, YAML errors, and duplicate filenames.

The `/sessions/<session>/mnt/` path below changes every session — read it from the folder-access confirmation rather than copying the example. A wrong path fails loudly, so this is a stumble, not a risk.

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
- `cssclass: timeline` on [[The Demon War]] — used by a theme.
- `ddb:` frontmatter — D&D Beyond character links.
- `Templates/` — Person, Location, Group, Event, Suggestion. These match the conventions above and are wired to both the core Templates plugin and Templater, where Nic has hotkeys bound to them. **If a convention changes, update these too**, and don't rename or move the files or the hotkeys break.
- `Suggestions/Suggestion Box.md` — the header and divider line are instructions for other players. Only ever clear text *below* the divider; never rewrite the header.
- `Suggestions/Suggestion History/` — a permanent record. Never edit or delete an entry after the fact; if a suggestion is later reversed or ruled on, write a new entry.
- Nic reorganizes and renames files himself. After a rename, Obsidian fixes wikilinks but **not plain-text prose mentions** — sweep for those.

`Area:` and `Favorability:` are *not* wired to any plugin. When converting old notes, fold them into the body as `**Region:**` and `**Disposition:**` rather than dropping the data.

## Name discrepancies — settled

Grant's [[Prelude for Thalrik Lastfeast]] spells several names differently from the vault. Nic has ruled on all of them. **Canonical forms:**

[[Aeralath]] · **[[Golden Plains|The Golden Plains]]** · [[Magus Trollbeater]] · [[Loryn Malcovitch|Malcovitch]] · [[Whisperwood]] · [[Kelara]] · [[Ishtir Marsh|Ishtir]] · [[Blackwaste]]

The vault spelling won everywhere except **Golden Plains**, which was renamed from "Golden Planes" to match the prelude. Each losing spelling is kept as an alias so older links still resolve — do not "fix" them by renaming.

When Grant's wording conflicts with Nic's own account, **Nic's account wins.** The bulette night in [[Thalrik's Road to Stonehold]] is the worked example.

**The map wins on place names.** `Map of Estrana.webp`, embedded on [[Estrana]], is authoritative for the spelling of locations. **[[Silnothas]]** was renamed from "Silnothis" to match it, with the old spelling kept as an alias — same pattern as Golden Plains. Places drawn on the map with no note simply have not come up in play; that is expected and not a gap to fill.

**The calendar.** **A.P. stands for *At Peace***, counted from the end of the [[Alnoria]]–[[Rorinden]] war about a thousand years ago. Campaign 1 ran 1016–1017 A.P., about one year of in-game time. [[Aeralath]]'s defeat closes the A.P. count and starts the **Dawning Era (D.E.)**, named for [[The Dawning]]. 1017 A.P. is 1 D.E.; Panrelta is set in **10 D.E.** Write dates in the `10 D.E.` form, parallel to `1017 A.P.` [[Estrana]] is the authoritative note.

## Open questions

- "shae de claw" and "zogmoi" — spellings unknown, from the elder-entity mention in session 28
- **[[Yorrisk]] is identified** — a developing town [[House Keroskav]] and Iron Oak [[House Dufrey]] are at war over, and where [[The Maiden]] said she would meet the party. "Upon the dawning" points at the tenth [[The Dawning|Dawning]], so this is now a place *and* a deadline. Still open: whether the battle [[Mirna Girbwood]] showed [[Thol]], [[Beemo]] and [[Gribnik Mossfoot]] there is memory, prophecy or fabrication
- Name of the arcane college [[Davynn Brindleknot|Davynn]] founded in the [[Blackwaste]] — the prelude marks it TBD
- Whether [[The Maiden]]'s 10,000 gold was paid or the apex griffon heart delivered
- Whether [[The Collector]] works for [[The Maiden]] — the centaur hooves suggest yes
- [[Beemo]], [[Falstad Firebeard]] and [[Gegga]] previously shared one `ddb:` URL; Nic has since corrected these
- **Why [[Aeralath]] wanted [[Queensbane]] collected.** She was helping [[The Sons of Thunder]] gain power specifically so they would gather the fragments of the one weapon that can harm her. The reason is unrecorded and should come with the Campaign 1 summary

## Pending work — the Campaign 1 summary

**Reed** — Campaign 1's DM, the creator of this world, and [[Beemo]]'s player in Panrelta — is writing a summary covering **the final three levels of Campaign 1**. As of August 2026 it is **32 pages** and he estimates it could reach **close to 50** before it is done, so **do not expect it soon.** The empty `Session Notes/Campaign 1/Campaign 1 Summary.md` is the placeholder for it.

Until it arrives, the Campaign 1 notes are frozen in a **mid-campaign** state and that is deliberate. Do not "fix" these by inference:

- [[Aeralath]] is listed as sealed and "expected to return within months"
- [[Queensbane]]'s attunement checklist has [[The Beastlands]] marked *current arc*, with four planes unchecked
- [[Timeline]] ends at [[Into the Beastlands]] — *current*
- [[The Sons of Thunder]] carries a stale "Current objective" section

**When it arrives:** create event notes in `Events/Campaign 1/Events/`, file new people and places into existing folders, and update [[Timeline]], [[Queensbane]] and [[00 - Campaign Index]]. Work through the loose threads on [[Timeline]] and mark which the ending resolves — including **why [[Aeralath]] wanted [[Queensbane]] collected**, which is the big one. Replace the stale sections listed above.
