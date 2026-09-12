# Changelog

## 1.0.1 - 2026-09-11

Bug fixes.

- MAME now reliably comes to the front when you launch a machine, instead of sometimes
  opening behind DJCJ Arcade or another app, or coming up with a greyed-out title bar
  that clicking on it would not fix
- Typing in the machine and software lists now jumps only to matching names, instead of
  also searching every other visible column and landing on something unexpected
- Video snaps no longer keep playing after you launch a machine, which could happen when
  double-clicking a machine that was not already selected

## 1.0 - 2026-09-06

First public release.

- Browse MAME's full catalog: every machine and every software title, with sorting,
  filtering, and multi-level sort
- Drill into any machine that has software and browse its titles
- Full-text search across machines and software
- Know what you actually have: a Have column and an availability filter, backed by
  auditing your files against MAME itself (File → Audit Machines, File → Audit
  Software Collection)
- Launch machines and software directly from the app, with quick per-launch checkboxes
  for things like fullscreen and artwork
- Loadouts: save which disk goes in which drive for a multi-drive machine, so it starts
  up ready to go
- A right-hand viewer pane for video snaps, manuals, box art, and other reference
  material from the EXTRAs and Multimedia packs, with configurable channel ordering
- Launch Codes: a full view into MAME's layered settings for any machine, with a built
  in editor that knows what your installed copy of MAME actually supports
- Launch Decisions: build your own quick-access checkboxes and dropdowns for any
  command line option, shown in the launch footer
- Collections, smart collections, and collection folders, with drag and drop, favorites,
  and multi-select
- Export a collection to a self-contained zip file
- Verify Database, to check the catalog file for the kinds of problem a bug could leave
  behind
- Back up and restore the database
- Universal build: native on both Apple Silicon and Intel Macs
