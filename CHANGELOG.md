# Changelog

## 1.1.0 - 2026-09-28

A Setup Wizard, ROM checks for software titles, and a clearer MAME pane.

- A new Setup Wizard walks you through getting started: finding MAME, building the catalog,
  choosing a working folder, pointing at your machine files, adding Category and Genre, and
  checking your ROMs. It opens on its own if you haven't built a catalog yet, and you can
  open it at any time from Get Started in Settings
- If you start setup and leave it unfinished, the main window shows a "Setup isn't
  finished" notice with a button to pick up where you left off
- Setup steps that depend on each other now wait for each other to finish, and the same
  step can no longer be started twice
- Software titles now have a ROMs section in their Details channel, like machines do, and
  Check ROMs in the Machine menu works for a selected software title as well as a machine.
  Titles that come on several disks are checked in full
- Every row in a ROMs section now has a Reveal in Finder button, which is greyed out when
  the file wasn't found
- The MAME pane in Settings now starts by telling you which MAME DJCJ Arcade is using, and
  says plainly if it can't find one, if the one it knows about has moved, if it won't run,
  or if it's missing SDL. Homebrew's copy and any other copy are offered as equal choices,
  and the Homebrew install steps only appear when there's no MAME at all
- Expanding or collapsing a parent machine no longer makes the list jump back to whatever
  was selected. The list only scrolls when it's replaced entirely, for example by a new
  filter, sort, or search, and then it keeps the selected row where it was on screen
- Collapsing a parent machine while one of its clones is selected now selects the parent

## 1.0.3 - 2026-09-14

One fix.

- A video snap could keep playing behind MAME after launching a machine, so you had to
  switch back to DJCJ Arcade, pause it, and return to the game. Most likely to happen when
  the drive holding your files was asleep and took a while to wake up

## 1.0.2 - 2026-09-12

A crash fix, and some changes to make things easier to find.

- Fixed a crash when exporting a collection to a folder you do not have permission to write
  to, or to a disk with no room left — it now tells you what went wrong instead of quitting
- The search field now sits directly above the machine list, rather than at the far right of
  the window away from everything else that acts on that list
- The channel selector is now labelled "Channel:" and sits on its own bar with the Previous
  and Next buttons, so it reads as a control you can change rather than a heading
- The panes can no longer be dragged narrow enough to push a toolbar button over the pane
  beside it, or to break the channel label apart

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
