# Changelog

## 1.2.1 - 2026-10-29

Fixes for libraries and HBMAME.

- Switching libraries could leave two copies of DJCJ Arcade running, most often when the
  switch came from New Library…, Convert to Library Folder…, or the offer to create an
  HBMAME library. The old copy now always quits before the new one starts, and if the quit
  is cancelled, nothing new starts. Restoring a database backup works the same way
- In an HBMAME library, MAME Launch Codes and the settings editor now use hbmame.ini, the
  file HBMAME actually reads, instead of mame.ini, which it ignores. The editor's default
  values now show up for HBMAME too. If your HBMAME Working Folder has a mame.ini but no
  hbmame.ini, MAME Launch Codes says so and offers to copy it across as a saved version
- With MAME and HBMAME sets in the same folder, Set Up From Folder… now picks the sets for
  the library's own emulator. An HBMAME library no longer gets MAME's ROMs, and a MAME
  library no longer gets HBMAME's CHDs or BIOS folder. Software lists, EXTRAs, and
  Multimedia still come from MAME's sets, which HBMAME shares

## 1.2.0 - 2026-10-28

Launch in RetroArch, keep separate libraries for MAME and HBMAME, and find your artwork
more reliably.

### RetroArch

- DJCJ Arcade can now launch machines and software in RetroArch as well as MAME. It's off
  until you turn on Enable RetroArch support in the new Settings → RetroArch pane, which
  is also where you say where RetroArch is and which of its cores to offer
- With it on, the Launch area has MAME and RetroArch tabs, and the RetroArch tab has a
  Core menu. The right-click menu and the Machine menu gain Launch with MAME (Option
  Command L) and Launch with RetroArch (Control Command L)
- Remember MAME or RetroArch for each machine, in Settings → RetroArch, switches the
  Launch area to the tab and core you last used for whichever machine you select
- Games run in RetroArch's MAME cores get every ROM folder you've set, so clones from a
  merged set, and machines whose CHDs live in a separate folder, start properly. Cores that
  only take a single zip, like FinalBurn Neo, are given the machine's zip, or one from a
  ROM folder you set for that core
- The core list starts with Arcade (MAME), FinalBurn Neo, MAME 2016, and MAME 2003-Plus.
  You can add, remove, rename, and reorder cores, and give each one its own ROM folder and
  extra command-line arguments, such as a shader
- Games launched from DJCJ Arcade no longer start paused. RetroArch otherwise pauses a
  game it thinks isn't in front, and when another app starts it, it can start that way.
  Only DJCJ Arcade's own launches are affected; your RetroArch settings aren't changed
- A new RetroArch Launch Codes channel shows exactly what will be handed to RetroArch:
  the game file, the settings applied for that launch only, and the full command line.
  Copy also writes the files the command uses, so you can paste it into Terminal and run it
  yourself. The existing Launch Codes channel is now called MAME Launch Codes
- Variants: hacks and alternate versions that only some cores have, such as 1942c64 under
  1942, can be added to a machine on the RetroArch Launch Codes channel, searching your
  cores' own game lists as you type. Software titles can take a file instead, such as a
  fan translation. Choose between the original and its variants from the new Version menu
  on the RetroArch tab
- When a RetroArch launch fails, the message leads with RetroArch's own errors rather than
  its routine warnings, and offers Switch to MAME. Quitting RetroArch normally isn't
  reported as a failure
- Check ROMs now notes that it checks with MAME, not with RetroArch's cores, which may need
  different ROM sets

### Libraries

- You can now keep completely separate libraries, each with its own catalog, collections,
  favorites, play history, and settings, including its own emulator, file locations,
  Working Folder, and RetroArch setup. So MAME and HBMAME, or two versions of MAME, never
  mix
- Switch between them from DJCJ Arcade → Switch Library…, from the library strip at the
  bottom of the sidebar, or by holding Option while DJCJ Arcade opens. Choosing one
  restarts DJCJ Arcade into it
- Your existing setup carries on as your first library, called Default, exactly where it
  always was. Nothing is moved
- New Library… makes an empty library and opens it, with its own Setup Wizard. You choose
  its emulator as you create it, and can install MAME or HBMAME from Homebrew right there
- Each library's folder holds everything that library needs, its settings included, so it
  can be moved, copied to another Mac, or kept on an external drive. Open Existing… adds
  one to your list
- The Libraries window's More menu can rename a library, show it in the Finder, remove it
  from the list, or move it to the Trash, which asks first and can be undone from the
  Trash. Convert to Library Folder… copies the original Default library into a folder of
  its own, leaving the original in place
- If the library DJCJ Arcade last had open can't be found, for example because its drive
  isn't connected, the Libraries window opens instead of a different library
- Each entry in the Log now says which library it came from

### HBMAME

- HBMAME can be installed and updated from inside DJCJ Arcade, the same way as MAME, from
  Settings → MAME or when you create a new library. It comes from estefan's Homebrew
  collection, and the About box now thanks him for making HBMAME available on the Mac
- Choosing HBMAME in a library whose catalog was built from regular MAME suggests making an
  HBMAME library instead, since switching would replace that catalog
- Choosing an app such as HBMAME.app as your emulator now works, including finding the SDL
  library that comes inside it
- The Working Folder's default location button now uses the right folder for the emulator
  you've chosen, and says which one, rather than always using MAME's

### Artwork and files

- Artwork and video that were in your EXTRAs or Multimedia folder but showing as missing
  are now found, including files named snaps.zip rather than snap.zip, zips made with the
  Finder's Compress, and JPEG pictures
- Settings → Assets now says why anything it can't find is missing, with a Set Location…
  button, and the new Settings → Assets (Advanced) pane lets you point each of the 37 kinds
  of asset at its own zip or folder, or put them all back to Automatic
- Machine Files has a new, optional BIOS & Device ROMs folder, for ROM sets that keep those
  files separately. Set Up From Folder… finds it too
- Rebuilding the catalog no longer fails with "Not a directory" when a folder it reads,
  such as MAME's hash folder, is a symbolic link
- The Setup Wizard no longer warns about a version mismatch when your ROM folder and your
  MAME are the same version written differently, such as 0.289 and 0.289.4

### Installing MAME or HBMAME

- Cancel now stops a Homebrew install straight away, instead of the window staying stuck
  until the install finished on its own
- The install's details can now be selected and copied, and a new Copy Details button
  copies all of them

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
