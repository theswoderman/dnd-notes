---
name: new-session-note
description: Create a session prep note for an upcoming D&D session. Summarizes what happened last session, captures end-of-session game state (combat positioning, held actions, who's controlling what), and lists all open campaign threads for quick reference during play. Use when the user says /new-session-note, asks to prep for a session, or wants a recap before playing.
---

# New Session Note

Create a prep note for the next session of Pilgrims of Panrelta. The output is a practical reference for use during play, not a vault note. It should be scannable at a glance.

## Steps

### 1. Find the most recent session note

Session notes live in `Session Notes/Pilgrims of Panrelta/nic's notes/`, named `Session N.md`. Find the highest-numbered one. There are also notes in a `misc/` subfolder (the prelude, dream, and early catch-up notes) which are older and can be ignored for this purpose.

### 2. Read the sources

Read all three of these:

- **The session note itself.** Raw, informal, full of shorthand. This is the primary source for what happened and how the session ended.
- **The Panrelta Timeline** (`Lore/Panrelta Timeline.md`). Two sections matter:
  - The **Session log** table, which records what entity and event notes were created or updated from each session. Use this to find the event notes worth reading for a cleaner account of what happened.
  - The **Loose threads** section, which is the authoritative list of open campaign threads, already organized by category.
- **The event notes** created from that session (listed in the session log). These have the processed, structured version of the session's events. Read them for the summary, since the raw session note is often hard to follow.

### 3. Write the prep note

Create the file in the same folder as the session notes (`Session Notes/Pilgrims of Panrelta/nic's notes/`), named `Session [N+1] notes.md` where N is the number of the most recent session note. This seeds the file that will become the raw notes for the upcoming session. If the file already exists, do not overwrite it (the user may have started adding notes to it already).

Use this structure:

```
# Session [N+1] notes

## Last session (Session N)
[2-4 paragraph summary of what happened, drawn from the event notes rather than the raw session note. Plain language, enough to jog memory. Include the key beats, decisions, and revelations.]

## Where we left off
[The end-of-session state. Pull this from the RAW session note, especially the last few lines, which often have tactical/combat details:
- Where the party physically is
- What they were doing when play stopped (mid-combat? traveling? resting?)
- Combat state if applicable: positioning, held actions, ongoing effects
- Who is controlling which character if there are any guest/absent player swaps
- Any immediate decisions that need to be made when play resumes]

## Open threads

### Immediate
[Copy from the Panrelta Timeline's Loose threads > Immediate section. These are the things that are actively happening and might come up this session.]

### The hags
[From Loose threads > The hags]

### The Maiden and Yorrisk
[From Loose threads > The Maiden and Yorrisk]

### From the Collector
[From Loose threads > From the Collector]

### Longer running
[From Loose threads > Longer running]
```

The open threads section should be copied fairly directly from the Panrelta Timeline, since that list is already maintained and curated. Light editing for scannability is fine (e.g., trimming a long explanation down to a reminder), but do not drop threads or change their meaning.

### 4. Present the file

Send the file to the user so they can see it.

## Important

- This note has no frontmatter. It seeds the next session's raw notes file, so the user can add to it during play.
- If the target file already exists, tell the user and do not overwrite it.
- Do not process, update, or create any other vault notes while running this skill.
- The "Where we left off" section is the most important part for the user. The combat/tactical state at the end of a session is exactly what is hardest to remember weeks later. Pull every detail from the raw note's final lines.
