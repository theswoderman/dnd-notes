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

Create `Session [N+1] notes.md` in the same folder. If it already exists, do not overwrite it.

Use this structure:

```
# Session [N+1] notes

## Where we left off
[Bullet list of end-of-session state from the raw note's final lines:
- Where the party is and what they were doing when play stopped
- Combat state if mid-fight: positioning, held actions, ongoing effects
- Character swaps (who is controlling whom this session)
- Immediate decisions to make when play resumes]

## Open threads
[A single flat bullet list of every open thread from the Panrelta Timeline's Loose threads section, deduplicated and compressed. Each thread gets ONE bullet, one line. Lean on wikilinks — don't explain what the link already covers. Drop any thread that is purely background with no chance of coming up soon.]
```

**No last-session recap.** The "where we left off" section is enough to jog memory, and the event notes are a click away.

**Keep it short.** The open threads section is a deduplicated, compressed version of the timeline's loose threads, not a copy of it. The timeline organizes threads by category with full explanations; this note flattens them into a single list of one-liners. If a thread appears in multiple categories on the timeline, it gets one bullet here. If a bullet would need two sentences, it's too long.

### 4. Present the file

Send the file to the user.

## Important

- No frontmatter. This seeds the next session's raw notes file.
- If the target file already exists, tell the user and do not overwrite it.
- Do not touch any other vault notes.
- The whole note should be roughly 30-40 lines. If it's longer, compress harder.
