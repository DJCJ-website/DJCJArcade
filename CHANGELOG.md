# Changelog

## 1.2.0 - 2026-10-28

Launch in RetroArch, keep separate libraries for MAME and HBMAME, and find your artwork
more reliably.

- DJCJ Arcade can now launch machines and software in RetroArch as well as MAME. It's off
  until you turn on Enable RetroArch support in the new Settings → RetroArch pane, which
  is also where you choose which RetroArch cores to use. With it on, the Launch area has
  MAME and RetroArch tabs, and the right-click menu and the Machine menu gain Launch with
  MAME (Option Command L) and Launch with RetroArch (Control Command L)
- RetroArch games that MAME's own cores run get every ROM folder you've set, so clones
  from a merged set, and machines whose CHDs live in a separate folder, start properly.
  Cores that only take a single zip, like FinalBurn Neo, are given the machine's zip
- A new RetroArch Launch Codes channel shows exactly what will be handed to RetroArch,
  next to the existing Launch Codes channel, which is now called MAME Launch Codes
- RetroArch variants: hacks and alternate versions that only another core has, such as
  1942c64 under 1942, can be added to a machine on the RetroArch Launch Codes channel
  and picked from a new Version menu in the Launch area
- Libraries: you can now keep completely separate libraries, each with its own catalog,
  collections, favorites, settings, and Working Folder, so MAME and HBMAME, or two
  different versions of MAME, never mix. Switch between them from DJCJ Arcade → Switch
  Library…, from the library strip at the bottom of the sidebar, or by holding Option
  while DJCJ Arcade opens. Your existing setup carries on as your first library, exactly
  where it was
- HBMAME can be installed and updated from inside DJCJ Arcade, the same way as MAME, from
  Settings → MAME or when you create a new library. Thanks to estefan for the Homebrew
  HBMAME this uses
- A library you no longer want can be moved to the Trash from the Libraries window. It's
  never deleted outright, so you can get it back from the Trash
- Artwork and video that were sitting in your EXTRAs or Multimedia folder but showing as
  missing are now found, including files named snaps.zip rather than snap.zip, zips made
  with the Finder's Compress, and JPEG pictures
- Settings → Assets now says why anything it can't find is missing, with a Set Location…
  button, and the new Settings → Assets (Advanced) pane lets you point each kind of
  artwork at its own location
- Machine Files has a new, optional BIOS & Device ROMs folder, for ROM sets that keep
  those files separately
- Rebuilding the catalog no longer fails with "Not a directory" when MAME's hash folder is
  a symbolic link
- Choosing an app bundle such as HBMAME.app as your emulator now works, including finding
  the SDL library inside it
- The Working Folder's default location button now uses the right folder for the emulator
  you've chosen, and says which one, rather than always using MAME's
- The Setup Wizard no longer warns about a version mismatch when your ROM folder and your
  MAME are the same version written differently, such as 0.289 and 0.289.4
- Cancel now stops a Homebrew install of MAME or HBMAME straight away, instead of the
  window staying stuck until the install finished on its own. The install's details can
  now be selected and copied, with a new Copy Details button

## 1.1.1 - 2026-10-05

Hide BIOS sets, choose which columns show, and see your folders when adding to a collection.

- The Filter menu has a new Show BIOS option. BIOS sets, the system firmware that groups of
  machines share, used to sit in the machine list looking like games. They're now hidden
  unless you turn Show BIOS on
- You can now choose which columns the machine and software lists show. Right-click any
  column header and tick or untick the columns you want, or use View → Machine List Columns
  and View → Software List Columns. A column you hide comes back where it was when you show
  it again, and Restore Default Columns puts every column back the way it started
- The "Show icons in the machine list" checkbox in Settings → Assets is gone. Icons now have
  their own column, which you show or hide like any other. If you had icons turned on, they
  stay on
- When you right-click a machine or a software title, the collections you can add it to are
  now laid out like the sidebar, with each folder as a heading and its collections indented
  beneath it. Machine → Add to Collection groups them by folder as well
- New installs start with an Enable Cheats Launch Decision, off until you tick it. The
  cheats come from the cheat.7z file in your EXTRAs pack

## 1.1.0 - 2026-09-28

A Setup Wizard, ROM checks for software titles, and a clearer MAME pane.

- A new Setup Wizard walks you through getting started: finding MAME, building the catalog,
  choosing a working folder, pointing at your machine files, adding Category and Genre, and
  checking your ROMs. It opens on its own if you haven't built a catalog yet, and you can
  open it at any time from the DJCJ Arcade menu or from Get Started in Settings
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
