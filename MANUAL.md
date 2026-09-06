# The DJCJ Arcade Manual

This is the full walkthrough. If you just want to get going, the [README](README.md)
covers the basics in a few minutes. Come back here when you want to know what a
particular screen does, or why something works the way it does.

## Before you begin

You need three things installed before DJCJ Arcade is useful for anything beyond
browsing.

**MAME itself.** DJCJ Arcade doesn't include it. It reads MAME's catalog and hands the
actual work of running a machine over to MAME. The easiest way to get it on a Mac is
with [Homebrew](https://brew.sh):

```
brew install mame
```

You can also install MAME any other way you like and just point DJCJ Arcade at it. If
you're on an Intel Mac, see [Running on an Intel Mac](#running-on-an-intel-mac) below
before you run that command, since Homebrew's version of MAME no longer supports Intel.

**Your own ROM files.** None are included with this app, and none ever will be. You can
browse the whole catalog with nothing installed, so this isn't required just to look
around, but you can only play what you actually have.

**The EXTRAs pack, if you want the artwork and video.** This is a community assembled
collection of box art, video clips, manuals, and other reference material. It's
optional. The app works fine without it, and looks a lot better with it.

## Installing

Download the latest version from this repository's Releases page, open the disk image,
and drag DJCJ Arcade into your Applications folder. The app is signed and notarized, so
it opens normally. macOS still asks you to confirm the first time you run anything
downloaded from the internet, which is expected and not specific to this app.

## Running on an Intel Mac

DJCJ Arcade itself runs natively on an Intel Mac. The build in Releases is universal, so
nothing about DJCJ Arcade is any different for you. Getting MAME itself running takes a
few extra steps, though, since the MAME project has moved on from Intel faster than this
app has.

### Getting MAME

Homebrew's own MAME formula has dropped Intel support, so `brew install mame`, the easy
path recommended earlier in this manual, will not get you a working copy on an Intel Mac.
You'll need to find a build of MAME made for Intel Macs somewhere else, or build one
yourself from MAME's own source, and just point DJCJ Arcade at it.

This manual isn't going to point you to a specific build to download. Anything named here
would be out of date within months, and if the easy Homebrew path doesn't work for your
Mac, you're already past the point a document like this can safely hold your hand through.
Look for one the way you would for any software from outside official channels, and be
skeptical the way you would be anywhere else.

Whatever build you end up with, take note of its version number. Your ROM sets are tied to
a MAME version too, and Settings → Machine Files is already built to notice a mismatch
there: a ROM set built for a much newer MAME than the one you're actually running is a
common cause of things auditing as Imperfect or Bad that would otherwise check out fine.

### Getting past macOS's security prompts

Two separate pieces of software need your permission here, since neither one is notarized
by Apple the way DJCJ Arcade itself is: the MAME executable, and SDL, the library MAME
uses to talk to your screen, audio, and controllers. Installing MAME through Homebrew
normally installs a matching SDL for you as part of the same step; going around Homebrew
means installing SDL yourself too, from its own project's
[release page](https://github.com/libsdl-org/SDL/releases).

Expect this in two rounds, not one, and expect it to look like it failed the first time
through each round:

1. Try to run MAME. It won't open, with nothing more helpful than that.
2. Open System Settings → Privacy & Security. Near the bottom, there's now a button to
   open it anyway. Click it, try running MAME again, and this time macOS asks for your
   admin password before it will proceed.
3. MAME now runs, but immediately quits with a wall of text ending in something like
   `Library not loaded: @rpath/SDL3.framework/... library load disallowed by system
   policy`. That's expected. It means MAME itself is approved now, but the SDL framework
   it depends on isn't yet, and macOS won't load an unapproved framework any more than it
   would run an unapproved program.
4. Go back to System Settings → Privacy & Security. The same button is there again, this
   time for the SDL framework. Click it, and confirm with your password the same way.
5. MAME will now actually run.

Settings → MAME reports what it finds about SDL, but only checks when that pane loads.
Since none of the steps above change the path to your MAME executable, the pane won't
notice on its own that step 4 just happened. Leaving Settings and reopening it forces a
fresh check, which is a real if slightly clunky way to confirm you're done. We're looking
at adding a proper way to ask it to check again without having to leave and come back.

## The first thing you'll see

The catalog starts out empty, because DJCJ Arcade doesn't come with one built in. Choose
**Rebuild Catalog…** from the File menu, or click the button on the empty screen. This
asks your installed copy of MAME to list everything it supports, reads its software list
files, and builds a search index from all of it. It takes about twenty seconds and
produces a database around 58 MB. You'll see progress and a log while it works, and you
can cancel partway through without losing the catalog you already had, since the whole
thing runs as one step that either finishes or doesn't happen at all.

Rebuild Catalog is also what you run again later, whenever you install a newer version
of MAME and want the app to catch up to it.

## Settings

Everything about where your files live and how the app behaves is in one place: **DJCJ
Arcade → Settings**, or **Command Comma**. It's a list of panes down the left side.
Here's what each one does.

### Get Started

A short numbered walkthrough of the panes that actually matter for getting up and
running, for when you'd rather be told what order to do things in than go pane by pane
yourself.

### General

Three unrelated settings that live here because they didn't belong anywhere else.

MAME sometimes prints a warning on a launch that otherwise runs fine, and DJCJ Arcade
can keep a record of those, plus any launch that fails outright, so you don't have to
run MAME from Terminal just to see what it's complaining about. That's the **Log**
section: turn it on, set how big it's allowed to grow before old entries get trimmed,
and choose whether it only captures warnings at startup or for the whole time you're
playing.

**High Scores** turns on one of MAME's own built in plugins that remembers your scores
between sessions. If you've already set up your own list of plugins by hand, this gets
added to it rather than replacing what you have.

**Option Guidance** is what powers the settings editor described later in this manual.
With it on, DJCJ Arcade reads MAME's own published source code so it can tell you more
about a setting than the running program alone would, like whether a value has to fall
in a particular range or be one of a fixed set of choices. It needs an internet
connection, and it depends on the app's understanding of MAME's source staying current.
If it's ever wrong, turn it off. You can still type any setting yourself either way.

### MAME

Where your copy of MAME actually lives. If you already have one installed, point at it
here. If you installed it with Homebrew, there's a button that finds it for you.
Otherwise, there's a button that opens Terminal and runs Homebrew's own official install
command where you can watch it happen and enter your Mac's password if it asks, which
DJCJ Arcade never sees.

This pane also checks for SDL, the separate software library MAME uses to talk to your
Mac's display, audio, and controllers. Installing MAME through Homebrew installs the
matching SDL for you automatically. If you installed MAME some other way, you may need
to install SDL yourself.

### Working Folder

One folder where DJCJ Arcade keeps all of MAME's settings on your behalf: the launch
option files DJCJ Arcade writes, plus the folders MAME itself uses while it runs, like
save states and high scores.

If you put this folder on an external drive alongside your ROMs, you can carry that
drive to a different Mac, point MAME at the same folder there, and everything picks up
exactly where it left off.

### Machine Files

Where your ROMs and CHDs live: separate fields for ROMs, CHDs, software list ROMs,
software list CHDs, and loose software. If you have a downloaded MAME collection sitting
in one folder, there's a **Set Up From Folder…** button that finds and fills in
everything it recognizes inside it, which you can still adjust afterward. Each field
shows the version number DJCJ Arcade found in the folder name, and a Rescan button
checks all of them against what's actually on disk right now.

If your folder names include a version, something like `MAME 0.289 ROMs (merged)`, the
app watches for a newer folder sitting next to it and offers to switch when you upgrade,
rather than quietly pointing at a folder that no longer matches your actual MAME
version.

### Assets

Where the EXTRAs pack and the separate Multimedia pack live, plus a summary of exactly
what each one gives you: the pictures and manuals for machines and software, the video
snaps, and whether categories and history write-ups are available. There's also a toggle
for showing small icons next to each machine in the list.

### Custom Files

MAME can read several kinds of file that change how it looks or behaves: controller
configuration files, crosshair graphics, extra plugins, translations. Some of these come
from MAME itself, and DJCJ Arcade finds those automatically. This pane is only for
pointing at files of your own on top of that, and every field here is optional.

### Channels

This is where you decide what shows up in the right hand viewer pane, described in more
detail below, and in what order. Every channel has a checkbox and a coverage number,
which tells you how many of your machines or software titles actually have that content
before you bother turning it on.

The full list, for machines: Video Snap, Snapshot, History, Launch Codes, Machine
Details, Title Screen, Cabinet, Marquee, Flyer, Control Panel, PCB, Logo, Boss, Ending,
Game Over, How To Play, High Score Screen, Select Screen, Versus Screen, Warning Screen,
Art Preview, Manual, MAME Info, Devices, High Scores, Setup, Commands, Soundtrack, and
Loadouts.

For software titles, the list is shorter: Launch Codes, Video Snap, Snapshot, Cover Art,
Software Details, Title Screen, Manual, and MAME Info.

Drag any of them into the order you want. The order controls what the Previous Channel
and Next Channel keyboard shortcuts cycle through. You can also set what happens when
the channel you're currently looking at has nothing for the selected item, separately
for machines and software titles.

### Launch Decisions

Covered in its own section below, since it's really a feature in its own right rather
than a simple settings pane.

### Setup Check

One screen that looks at everything DJCJ Arcade needs in order to launch something
successfully, and tells you what's actually wrong if anything is, rather than making you
guess. It checks MAME itself, your Working Folder, your Machine Files paths, MAME's
software definitions, plugins, translations, shader effects, artwork, sounds, cheats,
and any custom controllers, crosshairs, plugins, or translations you've pointed at.
Most of it is found automatically and needs nothing from you; this pane is where you'd
look if something isn't launching the way you expect.

## The main window

Down the left side is your library: All Machines, Favorites, and every collection and
folder you've created. The middle is a list, either machines or software depending on
what you're browsing. The right side is the viewer pane, showing whatever channel you
last had selected for whatever is currently highlighted in the middle.

At the top of the list, a green pill switches between Machines and Software, and shows
how many of each are currently in view.

## Browsing, sorting, and filtering

Click any column header to sort by it, and you can add a second sort underneath the
first, so you might sort by manufacturer and then by year within each manufacturer. The
Filter menu narrows the list down: hide clones, hide machines with an imperfect driver,
hide mechanical machines, and so on. Filtering never permanently removes anything from
the catalog. It's about what's showing right now, not what exists.

Machines that are really a whole platform rather than one single game, an Atari 2600 or
a Game Boy for instance, can be opened up to show everything that runs on them. Double
click in, or use the arrow next to its name, and you get that platform's own software
list instead of one line in the machine table.

The search box in the top right finds things by name across the whole catalog. Command F
jumps straight to it.

## Knowing what you actually have

The catalog describes everything MAME supports, which is not the same as everything you
own. Every machine and title has a **Have** column, and a filter that shows only the
things you can actually play right now.

To fill that column in, MAME needs to check your files against what it expects for each
machine, which the app calls an audit. **File → Audit Machines** and **File → Audit
Software Collection** are two separate operations, run separately, because auditing
software takes a good deal longer than auditing machines and not everyone wants to pay
that cost every time. For any single machine, its own Machine Details screen shows you
exactly which files it needs, which ones were found, where each one was found, and
whether MAME itself considers the result good.

A cartridge based system like the Atari 2600 or the Genesis doesn't really have a ROM to
verify the way an arcade board does, so its availability comes from whether you own real
software for it instead.

## Collections

You can group machines and software into collections, and put collections inside
folders, and put things into as many collections as you like at once.

There are two kinds. A **regular collection** holds exactly what you drag into it,
nothing more and nothing less. A **smart collection** describes what belongs in it, and
fills itself in and stays current on its own, the same way a saved search would.

When you build a smart collection, you're choosing whether it should match **all** or
**any** of a list of rules, and each rule picks a field, a comparison, and a value. The
fields you can build a rule against are: Name, ROM Name, Manufacturer, Year, Players,
Driver Status, Availability, Original or Clone, Category, Genre, Device, Mechanical,
BIOS, Runnable, Has Software List, Has Clones, Driver Source File, Plays, Last Played,
and Collection. So "everything Atari made in the seventies and eighties" is a rule on
Manufacturer and a rule on Year, matched together.

A folder's own count includes everything nested inside it, including any smart
collections inside it, counted once even if a machine happens to belong to more than one
collection that folder contains.

If MAME's own updates rename or remove something you'd filed away, it stays in your
collections rather than vanishing. It shows up greyed out with an explanation, until you
either move it under its new name or remove it yourself.

**Favorites** is a star column available everywhere in the app, and a dedicated
Favorites item in the sidebar collecting everything you've starred.

## The viewer pane and Machine Details

The panel on the right shows whatever channel is currently selected for whatever machine
or title is highlighted. Switch between channels with the picker at the top of the pane,
or with Previous Channel and Next Channel from the Channels menu.

**Machine Details** is the channel with the basic facts: ROM name, year, manufacturer,
player count, driver status, your Have status, how many times you've played it, and its
category and genre if the EXTRAs pack has them. Underneath that is the ROM checklist
described above, with a Check ROMs button to audit that one machine on the spot.

Most of the other channels come from the EXTRAs and Multimedia packs: photographs of the
cabinet, marquee, flyer, control panel, and PCB; screenshots of the title screen, game
over screen, and several others; the manual as a scanned PDF; and video snaps, played
back live rather than pre-converted to another format.

**MAME Info**, **History**, and **High Scores** are longer written references, parsed
out of files the EXTRAs pack provides. **Devices** shows the individual parts inside a
machine, each with its own photo where one exists. **Soundtrack** plays ripped music and
sound effects for the machines the Multimedia pack covers.

## Launching

Select something and click **Launch**, or press **Command L**. You don't need to leave
the list to do it, and the app always shows you what's about to run before it runs it.

Next to the Launch button is a row of checkboxes and dropdowns, described fully in the
next section. What you see there depends entirely on what you've set up in Settings →
Launch Decisions, which starts out with a couple of common ones already in place and
grows however you want from there.

If you select a copy of MAME's history that has more than one disk drive, like an old
home computer with a floppy drive or two and maybe a hard disk, you can save a
**Loadout**: which disk goes in which drive, saved together and named. Save as many as
you like for one machine. Launching directly applies your saved Loadout automatically:
no prompt at all if you've only saved one, or a quick choice if you've saved more than
one.

Some software titles were released for more than one machine, a cartridge compatible
with a couple of different console revisions, for instance. For those, **Machine → Open
With…** (Command O) lets you choose which machine to launch it on, the same idea as
choosing which app opens a file. If only one machine plays that title, DJCJ Arcade just
launches it there directly and skips asking.

## Launch Decisions

This is the part that takes the most explaining, so it gets its own walkthrough.

Launch Decisions are the quick-access checkboxes and dropdowns that appear right next to
the Launch button. You build them yourself in Settings → Launch Decisions: give one a
name, choose whether it's a **Checkbox** or a **Dropdown**, and decide what command line
text gets added when it's on versus off (a dropdown works the same way, just with more
than two choices instead of only two).

Two start out already there for you: **Fullscreen**, and **Artwork**. Beyond those two,
what you see is entirely up to you. As an example, one setup might add a Checkbox called
Uneven Stretch that writes `-unevenstretch` when ticked and `-nounevenstretch` when not,
and a Dropdown called Art offering Full Art, Overlay Only, No Art, and a fourth option
that defers to whatever your regular settings already say.

While you're editing one of these, a row of buttons above the list, things like ROMs,
Working Folder, Artwork Path, and Config Directory, let you click a real path into your
command text instead of typing it out and risking a typo. Reorder decisions with the
arrows, which matters beyond just how they're displayed: this is the actual order their
text gets added to MAME's command line, so if two enabled decisions ever write the same
option, whichever one is lower in the list wins.

Turning off a decision's **Ask at launch** checkbox removes it from the footer entirely,
for both the ticked and unticked text, and lets MAME's own settings files decide that
question on their own instead.

## Launch Codes

MAME reads its settings from several files, in a fixed order, and each one can override
whatever came before it: one file for everything, then one for every machine sharing a
particular kind of screen, then one for everything sharing a chipset, and finally one for
the single machine you're looking at. It's a genuinely powerful system, and it's also
easy to lose track of, since the setting you're hunting for could be sitting in any one
of those files, and something further down the chain might be quietly overriding it
without telling you.

**Launch Codes** is a channel that lays this whole chain out for whichever machine is
selected, in order, color coded, and tells you plainly which files are actually active
for this machine and which ones are sitting empty. You can save several named versions
of each file, so "vector with bigger beams" becomes a version you switch on and off
rather than a change you make and then have to remember you made.

Underneath all of that, DJCJ Arcade always works out its own set of paths for you
automatically, based on your Settings and where MAME is installed, and that beats
everything above it unless you turn it off.

### Saving and switching between versions

Every version you save is a real, separate file on disk, not an entry in a database or a
snapshot the app is managing invisibly somewhere. They live inside your Working Folder,
in a folder called "DJCJ Arcade ini Versions," with its own subfolder for each file in
the chain, so `mame.ini`'s versions and `vector.ini`'s versions never mix.

Nothing anywhere records which version is currently the active one. Instead, DJCJ Arcade
compares the real file MAME is actually about to read against the content of every saved
version, and whichever one matches exactly is the one shown as active. That has a genuinely
useful side effect: if you edit the live file directly and never save your changes as a
version, nothing matches, and the app honestly shows you that what MAME is about to use
right now isn't saved anywhere under a name yet.

Picking a different version from the dropdown works the same idea in reverse: it copies
that version's file over the live one. The live file is always a copy of some version,
never something you edit in place and save back over its own source.

**Add** starts a brand new version from a blank file. **Save Current Settings as a
Version…** does the opposite: it takes whatever is live right now, including any edits
you haven't saved anywhere yet, and copies it into a new version under a name you choose.
That one button covers both "save what I've been fiddling with" and "branch off from
where I am right now." **Edit…** opens the editor described below on that version.
**Reveal in Finder** shows you the real file.

**Delete a Version…** doesn't actually delete anything. It renames the file so it drops
out of the app's own list, with the original name and a timestamp kept in the new
filename, so undoing an accidental delete is a trip to Finder rather than a lost
afternoon. If the version you delete happens to be the active one, the live file it was
backing is removed too, and whatever sits beneath it in the chain takes over.

One version usually shows up on its own, with nothing for you to do: DJCJ Arcade asks
your installed MAME for its own untouched, factory settings and saves them for you
automatically, named something like "MAME 0.289 defaults." That gives you a genuine,
unedited baseline sitting there whenever you want to compare against it or fall back to
it.

### Editing a file

Click **Edit…** on any file in the chain and a plain text editor opens, showing that
file exactly as MAME will read it, changes and all, since it's a real text file on your
disk rather than a form standing in for one.

**The left pane is an index of every setting your installed copy of MAME actually
understands, not a fixed list built into the app.** It's built by literally asking MAME:
DJCJ Arcade runs your installed copy with `-showusage`, which is MAME's own way of
listing everything it supports, and reads the result. That means the list you see always
matches the exact version of MAME on your Mac, options included. If you're on an older
or newer MAME than the machine that built this manual, your list may look slightly
different, and that's expected.

Search it from the box at the top, or use the sort menu to view it four different ways:
by **Category**, the same grouping MAME's own documentation uses; **A-Z**; **Favorites**,
your own starred settings; or **Most Used**, ranked by how often you've actually reached
for each one. Click the star next to any setting to add or remove it from Favorites.

Click a setting in the list, or place your cursor on one already written in the file, and
a bar appears above the text showing its name, its category, and a short description of
what it does. The description comes from your installed copy of MAME, and gets more
detail still when Option Guidance (Settings → General) is turned on, since that lets DJCJ
Arcade also read MAME's own published source code for things like a value's valid range
or fixed set of choices.

That same bar is also where you set the value, and it changes shape depending on what
kind of setting you've picked. A plain on-or-off setting gets a real switch. A number with
a known range, like a percentage, gets a stepper instead of a bare text field. A setting
with a fixed set of choices, like `auto`, `opengl`, `bgfx`, `accel`, `soft`, or `none` for
video output, gets a dropdown listing exactly those choices rather than leaving you to
remember or guess them. A folder or file path gets a path chooser. Anything else gets a
plain text field. The button next to it reads **Insert** for a setting that isn't in the
file yet, or **Update** once your cursor is sitting on a line that's already there.

You can also just type directly into the file the way you would in any text editor, and
the app suggests completions as you go, drawn from that same live list.

**Enforce Categories**, checked by default, keeps every setting filed under the right
category comment automatically, the same section headings you see in the left pane and
in the file itself, like `# CORE VECTOR OPTIONS`. Drag a setting to reorder it and this is
what snaps it into place under the correct heading rather than leaving it wherever you
dropped it. It also catches settings you type or paste in by hand: once you've finished
typing a real setting's name, DJCJ Arcade relocates it under its proper category on its
own, creating that category's heading first if the file doesn't have it yet. Turn this
off if you'd rather the file's order stay exactly as you left it.

If you write something MAME doesn't recognize at all, the editor tells you right there,
and gives you the likely reasons: a typo, an option from a version of MAME other than the
one you have installed, or hardware you don't currently have connected.

## Other things on the Machine menu

**Copy Command Line** (Shift Command C) copies the exact command that would run if you
launched right now, including every setting from every layer of the chain and any Launch
Decisions currently ticked. Useful for troubleshooting, or for sharing exactly what you
ran with someone else.

**Download Manual…** (Shift Command D) fetches a manual for the selected machine when
one isn't already sitting in your EXTRAs pack.

**Reveal in Finder** (Shift Command R) shows the selected machine or title's files in the
Finder.

**Check ROMs…** (Option Command V) runs the same file-by-file audit as the Check ROMs
button on Machine Details, without leaving the list.

## Exporting a collection

Right click any collection, or use the Collections menu, and choose **Export Collection
to Zip…**. This builds one self-contained zip file sized to exactly what that collection
actually needs, rather than pulling in your whole library. It mirrors DJCJ Arcade's own
folder layout, so the result works on its own: a portable ROM set you can hand to a
friend, copy to a Raspberry Pi, or diff against your main library later.

## Verify Database and backups

**File → Verify Database…** checks the catalog file itself for the kinds of problem a
bug could theoretically leave behind: broken links between tables, a collection nested
inside itself, a smart collection with rules that no longer make sense, duplicate
collection names, and a few others. Most people will never need this, and it exists so
that if something ever looks wrong, there's a real answer rather than a guess.

**File → Back Up or Restore Database…** saves a copy of your whole catalog, your tags,
your collections, your play counts, everything, to a file of your choosing, and can
restore from one later. Worth doing before a big change you're not sure about, or just
now and then for peace of mind.

## Keyboard shortcuts worth knowing

| Shortcut | Does |
| --- | --- |
| Command L | Launch the selected machine or title |
| Command O | Open With, when a title runs on more than one machine |
| Command F | Jump to the search box |
| Command Comma | Open Settings |
| Shift Command R | Reveal the selected item's files in Finder |
| Shift Command C | Copy Command Line |
| Shift Command D | Download Manual |
| Option Command V | Check ROMs for the selected machine |
| Shift Command A | Audit Machines |
| Option Shift Command A | Audit Software Collection |
| Option Shift Command R | Rebuild Catalog |
| Command R | Refresh EXTRAs Folder Data |
| Shift Command V | Verify Database |
| Shift Command B | Back Up or Restore Database |

Full menus have more, this is just the short list of the ones you'll reach for most.

## If something goes wrong

Settings → General lets you turn on a Log of anything unusual MAME reports on launch,
including outright failures. **Window → Log** shows it, and **Reveal Log in Finder** and
**Clear Log** are right next to it if you need to send someone the actual file or start
fresh.

If you run into a real bug, this repository's Issues page is the place to report it.
