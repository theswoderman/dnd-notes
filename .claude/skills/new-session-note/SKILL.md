---
name: new-session-note
description: Create a session prep note for an upcoming D&D session. Captures end-of-session game state and lists open campaign threads as a quick-reference cheat sheet for during play. Use when the user says /new-session-note, asks to prep for a session, or wants a recap before playing.
---

# New Session Note

Create a short prep note for the next session of Pilgrims of Panrelta. This is a cheat sheet for use during play: short, scannable, and lean on wikilinks so the reader can click through for detail. The whole note should fit on a screen or two.

## Steps

### 1. Find the most recent session note

Session notes live in `Session Notes/Pilgrims of Panrelta/nic's notes/`, named `Session N.md`. Find the highest-numbered one. Ignore the `misc/` subfolder.

### 2. Read the sources

- **The raw session note.** The last few lines are the main source for end-of-session state.
- **The Panrelta Timeline** (`Lore/Panrelta Timeline.md`). Read the **Loose threads** section for open campaign threads.

### 3. Write the prep note

Create `Session [N+1].md` in the same folder. If it already exists, do not overwrite it.

Use this structure:

```
# Session [N+1]

## Where we left off
[Bullet list of end-of-session state from the raw note's final lines:
- Where the party is and what they were doing when play stopped
- Combat state if mid-fight: positioning, held actions, ongoing effects
- Character swaps (who is controlling whom this session)
- Immediate decisions to make when play resumes]

## Open threads
[A flat bullet list of open UNKNOWNS and UNRESOLVED QUESTIONS from the Panrelta Timeline's Loose threads section. Focus on things the party doesn't understand yet, not things they already know are happening. "Torin called Beemo 'little shadow' without knowing why" is good — it's a mystery. "The hags are in the party's dreams" is not — that's established fact, not an open question. When in doubt whether something qualifies, ask the user rather than including it. Each thread gets one bullet, one line. Lean on wikilinks.]
```

**No last-session recap.** The "where we left off" section is enough to jog memory, and the event notes are a click away.

**Keep it short.** The open threads section is not a copy of the timeline's loose threads. It is a filtered, compressed selection of the unknowns and unresolved questions. Drop established facts, known threats, and anything that is purely background. If a bullet would need two sentences, it's too long. If something is borderline, ask.

### 4. Present the file

Send the file to the user.

## Important

- No frontmatter. This seeds the next session's raw notes file.
- If the target file already exists, tell the user and do not overwrite it.
- Do not touch any other vault notes.
- Target under 300 words. If it's longer, compress harder.
