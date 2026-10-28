# The DJCJ Arcade Manual

This is the full walkthrough. If you just want to get going, the [README](README.md)
covers the basics in a few minutes. Come back here when you want to know what a
particular screen does, or why something works the way it does.

## Before you begin

DJCJ Arcade needs three things before it's useful for anything beyond browsing.

**MAME itself.** DJCJ Arcade doesn't include it. It reads MAME's catalog and hands the
actual work of running a machine over to MAME. You don't need to install it before you
start: the first step of the [Setup Wizard](#the-first-thing-youll-see-the-setup-wizard)
looks for a copy on your Mac, and if there isn't one, installs it for you through
[Homebrew](https://brew.sh), a free package manager for the Mac. If you'd rather do that
yourself, it's one command in Terminal:

```
brew install mame
```

Either way works on both Apple Silicon and Intel Macs. You can also use a copy of MAME
from anywhere else, one you downloaded or built yourself, and just point DJCJ Arcade at
it. See [Using a MAME from somewhere other than Homebrew](#using-a-mame-from-somewhere-other-than-homebrew)
below if you do.

**Your own ROM files.** None are included with this app, and none ever will be. You can
browse the whole catalog with nothing installed, so this isn't required just to look
around, but you can only play what you actually have.

**The EXTRAs pack, if you want the artwork and video.** This is a community assembled
collection of box art, video clips, manuals, and other reference material. It's
optional. The app works fine without it, and looks a lot better with it.

Two more things are optional, and only worth reading about if you already use them:

- **HBMAME**, a version of MAME with thousands of homebrew games and hacks that regular
  MAME doesn't include. DJCJ Arcade can install it for you too, and works best with it in
  a [library](#libraries) of its own.
- **RetroArch**, if you'd like to run some games in it instead of MAME. See
  [Launching in RetroArch](#launching-in-retroarch).

## Installing

Download the latest version from this repository's Releases page, open the disk image,
and drag DJCJ Arcade into your Applications folder. The app is signed and notarized, so
it opens normally. macOS still asks you to confirm the first time you run anything
downloaded from the internet, which is expected and not specific to this app.

There are three downloads. The plain one is universal, running natively on both Apple
Silicon and Intel Macs, so if you're not sure which to pick, pick that one. The Apple
Silicon and Intel downloads are smaller, each holding only the version for that kind of
Mac.

### On an Intel Mac

DJCJ Arcade itself runs natively on an Intel Mac, and installing MAME through Homebrew
works there too, from the Setup Wizard or from Terminal. Expect it to take a good deal
longer than on Apple Silicon, though. Homebrew often has no ready-made MAME for Intel Macs,
so it builds MAME from its source code on your Mac instead, and MAME is a very large
program to build. That's normal: leave the install running until it finishes.

## Using a MAME from somewhere other than Homebrew

Any build of MAME works, whether you downloaded it, built it yourself, or got it some other
way. Point DJCJ Arcade at it in the Setup Wizard's MAME step, or in Settings → MAME.

Take note of its version number. Your ROM sets are tied to a MAME version too, and a ROM
set built for a much newer MAME than the one you're actually running is a common cause of
things auditing as Imperfect or Bad that would otherwise check out fine. The Setup
Wizard's Machine Files step warns you when the two don't match.

### SDL

MAME uses a separate library called SDL to talk to your screen, audio, and controllers.
Installing MAME through Homebrew installs a matching SDL for you as part of the same step.
Going around Homebrew means installing SDL yourself too, from its own project's
[release page](https://github.com/libsdl-org/SDL/releases). Settings → MAME tells you if
SDL is missing.

### Getting past macOS's security prompts

A MAME you downloaded yourself, and the SDL that goes with it, aren't notarized by Apple
the way DJCJ Arcade is, so macOS won't run either one until you approve it. A MAME
installed through Homebrew doesn't need any of this.

Expect it in two rounds, not one, and expect it to look like it failed the first time
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

Settings → MAME tells you whether MAME will run and whether SDL was found, but it won't
notice on its own that you've just approved something in System Settings. Click **Check
Again** in that pane once you're through step 4, and it will tell you whether you're done.

## The first thing you'll see: the Setup Wizard

The catalog starts out empty, because DJCJ Arcade doesn't come with one built in, so the
first time you open the app the **Setup Wizard** opens alongside the main window. It walks
you through everything DJCJ Arcade needs before your library appears, one step at a time,
with the steps listed down the left side.

1. **MAME.** The same MAME pane that's in Settings, described below. If DJCJ Arcade found
   MAME on its own, this step is already ticked and there's nothing to do. If there's no
   MAME on your Mac, this is where you install it, without going near Terminal.
2. **Build the Catalog.** Asks your installed copy of MAME to list everything it
   supports, reads its software list files, and builds a search index from all of it. It
   takes about twenty seconds and produces a database around 58 MB. You don't have to wait
   for it: start it, and carry on with the next steps while it runs.
3. **Working Folder.** One folder for MAME's settings and your save files, described
   under Settings below.
4. **Machine Files.** Where your ROMs and CHDs live. If your ROM folders are for a
   different version of MAME than the one you're running, this step warns you, since
   that's a common reason for machines showing as bad or missing when your files are
   actually fine. It compares the version numbers themselves, so a folder for 0.289 and
   a MAME that calls itself 0.289.4 count as a match.
5. **Category and Genre.** If you have an EXTRAs pack, this imports its lists that sort
   every machine into a category and a genre, adding those columns to the machine list and
   letting smart collections use them. Without an EXTRAs pack there's nothing to import,
   and the step says so.
6. **Check What You Have.** One button asks MAME which of your machines and then which of
   your software titles your files actually cover. When the machine check finishes, the
   machine list narrows to what you have files for. Nothing is removed: the Availability
   section of the Filter menu shows everything again whenever you like.
7. **Artwork and Video.** Optional. Where the EXTRAs and Multimedia packs live. If they
   sit beside your ROM folders, the Machine Files step may already have found them.

Each step's marker shows where it stands: a number for something still to do, a tick once
it's done, a spinner while it's running, and an hourglass when it's waiting for another
step to finish first. That last one means you can start checking your files, or importing
Category and Genre, before the catalog is finished building, and they'll start on their
own as soon as it is.

The markers are worked out fresh from your actual settings every time, so anything you set
up before, in Settings or an earlier run of the wizard, shows as done already. You can
also close the wizard at any point. Anything it started keeps running, and while setup
isn't finished, a **Setup isn't finished** bar sits at the top of the main window showing
what's still running, with a button to open the wizard again where you left off.

If you'd rather find your own way around, **Skip Setup** closes the wizard and stops it
opening on its own. Whether you skip it or finish it, it's always in the **DJCJ Arcade**
menu as **Setup Wizard…**, and in Settings → Get Started.

If you already have a catalog, from an earlier version of DJCJ Arcade for instance, the
wizard doesn't open on its own, and the app starts up just as it always has. A new
[library](#libraries) starts empty, so the wizard opens for it, and walks you through
setting that library up from scratch.

### Rebuilding the catalog later

Whenever you install a newer version of MAME and want the app to catch up to it, choose
**DJCJ Arcade → Rebuild Catalog…** (Option Shift Command R). You'll see progress and a log
while it works, and you can cancel partway through without losing the catalog you already
had, since the whole thing runs as one step that either finishes or doesn't happen at all.
Your favorites, collections, and play counts are never touched by a rebuild. If you have
more than one [library](#libraries), a rebuild only affects the one that's open.

## Settings

Everything about where your files live and how the app behaves is in one place: **DJCJ
Arcade → Settings**, or **Command Comma**. It's a list of panes down the left side.
Here's what each one does.

### Get Started

A short numbered checklist of the panes that actually matter for getting up and running,
for when you'd rather be told what order to do things in than go pane by pane yourself.
Each item is ticked off once it's done, with a button that takes you straight to the pane
that settles it. It's the same set of checks the Setup Wizard uses, so the two always
agree, and **Open Setup Wizard…** at the top opens the wizard if you'd rather be walked
through it one step at a time.

### General

A few unrelated settings that live here because they didn't belong anywhere else.

MAME sometimes prints a warning on a launch that otherwise runs fine, and DJCJ Arcade
can keep a record of those, plus any launch that fails outright, so you don't have to
run MAME from Terminal just to see what it's complaining about. That's the **Log**
section: turn it on, set how big it's allowed to grow before old entries get trimmed,
and choose whether it only captures warnings at startup or for the whole time you're
playing. **Search Engine** picks which site the search button on each log entry uses, for
looking up a warning you don't recognize.

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

Which copy of MAME DJCJ Arcade is using, and whether anything needs doing about it.

The pane opens with one sentence answering exactly that. When everything is working, it
names the version of MAME in use and where it is, with a badge showing whether SDL was
found, and there's nothing more to do. When it isn't, the sentence tells you which of four
different problems it is, because each one has a different fix:

- **No MAME found at all.** Install one using the steps at the bottom of the pane, or
  choose a copy you already have.
- **MAME isn't where it was.** If it's on a drive that isn't connected, connect it and
  click **Check Again**. Otherwise, choose a different copy.
- **MAME is there but won't run.** If you downloaded it yourself, macOS may be blocking
  it. See [Getting past macOS's security prompts](#getting-past-macoss-security-prompts)
  above.
- **MAME is missing SDL.** SDL is the separate software library MAME uses to talk to your
  Mac's display, audio, and controllers. Installing MAME through Homebrew includes it; if
  you installed MAME some other way, you may need to install SDL yourself.

**Check Again**, beside that sentence, looks again right away. It's useful after installing
MAME, connecting a drive, or approving MAME or SDL in System Settings.

Under **Use a different MAME**, Homebrew's copy and any other copy are offered side by
side as equal choices. **Homebrew's MAME** shows whether Homebrew has one installed, with
buttons to use it, update it to Homebrew's latest version, or install it. **Another copy** takes the path to any MAME
you have, whether you downloaded it, built it yourself, or got it some other way, and
**Choose…** lets you pick it in the Finder. You can choose an app, such as HBMAME.app, as
well as a plain program file: DJCJ Arcade finds the real program inside it, and the SDL
library that comes with it. Whichever one is in use is marked **In Use**.

**Homebrew's HBMAME** works the same way as Homebrew's MAME: **Use This** if it's
installed, **Update**, or **Install HBMAME**, which runs the install in a progress window.
HBMAME comes from a Homebrew collection kept by estefan, who made HBMAME available for the
Mac. If you choose HBMAME in a library whose catalog was built from regular MAME, DJCJ
Arcade suggests **Create an HBMAME Library** instead, since switching would replace that
catalog. **Use in This Library** switches anyway.

If there's no MAME on your Mac at all, a **Don't have MAME yet?** section at the bottom
gives you two steps:

1. **Install Homebrew…**, if you don't have it already. This opens Terminal and runs
   Homebrew's own official install command, where you can watch it happen and enter your
   Mac's password if it asks, which DJCJ Arcade never sees. Click **Check Again** when it's
   done.
2. **Install MAME.** This runs `brew install mame` for you, inside DJCJ Arcade, in a
   window that shows its progress, and installs the SDL that MAME needs along with it.
   When it finishes, DJCJ Arcade starts using that copy straight away. It can take a few
   minutes on Apple Silicon and a good deal longer on an Intel Mac, where Homebrew often
   builds MAME from its source code; see [On an Intel Mac](#on-an-intel-mac).

While an install or update runs, its progress window shows Homebrew's own output as it
goes. **Cancel** stops it straight away, though anything Homebrew had already finished
installing, like some of MAME's dependencies, stays installed. **Copy Details** copies
Homebrew's output, for looking up an error or sending it to someone.

Once DJCJ Arcade has found a copy of MAME, that section goes away. **Update** under
Homebrew's MAME works the same way, running `brew upgrade mame` in a progress window. After
updating MAME, rebuild the catalog so DJCJ Arcade catches up to it.

### Working Folder

One folder where DJCJ Arcade keeps all of MAME's settings on your behalf: the launch
option files DJCJ Arcade writes, plus the folders MAME itself uses while it runs, like
save states and high scores.

If you put this folder on an external drive alongside your ROMs, you can carry that
drive to a different Mac, point MAME at the same folder there, and everything picks up
exactly where it left off.

A button sets the folder to your emulator's own usual location, and says which emulator
that is: **Use MAME's Default Location**, or **Use HBMAME's Default Location** in a library
that uses HBMAME, so each one keeps its settings in its own place. A new library starts
with a Working Folder inside the library's own folder.

### Machine Files

Where your ROMs and CHDs live: separate fields for ROMs, CHDs, software list ROMs,
software list CHDs, loose software, and BIOS & Device ROMs. That last one is optional:
some ROM sets keep the BIOS and device files that many machines share in a folder of their
own, while MAME's own sets keep them with the other ROMs. Each field takes one folder. If you have a downloaded MAME collection sitting
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
snaps, and whether categories and history write-ups are available. If the pack has small
icons for each machine, they appear in the machine list's Icon column, which you can show
from View → Machine List Columns.

DJCJ Arcade looks for each kind of artwork under the names packs actually use, including
either spelling where packs differ, like `snap.zip` and `snaps.zip`. A zip works whether
its pictures sit at the top or inside one folder, which is what the Finder's Compress makes,
and pictures can be PNG or JPEG. Anything it still can't find is marked **Not Found**, with
a note saying why and a **Set Location…** button to point at it yourself.

### Assets (Advanced)

Every kind of asset DJCJ Arcade supports, all thirty-seven of them, each with its own
location. Each one starts on **Automatic**, which means DJCJ Arcade looks for it inside
your EXTRAs and Multimedia folders, and shows you where it looks. If an asset lives
somewhere else, or Automatic isn't finding it, **Choose…** points at the exact zip or
folder. **Automatic** puts a single asset back, and **Set All to Automatic…** clears every
location you've chosen here. **Change in Assets…** takes you back to the EXTRAs and
Multimedia folders themselves.

Whatever you choose here is what every part of the app uses: the viewer pane, the Assets
pane, and the artwork, cheat, and sample folders DJCJ Arcade hands to MAME. Exporting a
collection to a zip still reads the standard EXTRAs layout.

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

The full list, for machines: Video Snap, Snapshot, History, MAME Launch Codes, RetroArch
Launch Codes, Machine
Details, Title Screen, Cabinet, Marquee, Flyer, Control Panel, PCB, Logo, Boss, Ending,
Game Over, How To Play, High Score Screen, Select Screen, Versus Screen, Warning Screen,
Art Preview, Manual, MAME Info, Devices, High Scores, Setup, Commands, Soundtrack, and
Loadouts.

For software titles, the list is shorter: MAME Launch Codes, RetroArch Launch Codes,
Video Snap, Snapshot, Cover Art, Software Details, Title Screen, Manual, and MAME Info.
RetroArch Launch Codes only appears while RetroArch support is turned on.

Drag any of them into the order you want. The order controls what the Previous Channel
and Next Channel keyboard shortcuts cycle through. You can also set what happens when
the channel you're currently looking at has nothing for the selected item, separately
for machines and software titles.

### Launch Decisions

Covered in its own section below, since it's really a feature in its own right rather
than a simple settings pane.

### RetroArch

Off until you turn on **Enable RetroArch support**. Covered in
[Launching in RetroArch](#launching-in-retroarch) below.

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

At the bottom of the sidebar, a strip shows which [library](#libraries) is open. Click it
to switch to another, or to manage your libraries.

## Libraries

A library is a separate world inside DJCJ Arcade, with its own catalog, collections,
favorites, play history, and settings, including its own emulator, file locations,
Working Folder, and RetroArch setup. Only one is open at a time. Most people only ever
need one, but libraries are the way to keep things that shouldn't mix apart: MAME and
HBMAME, for instance, or two different versions of MAME with ROM sets to match.

If you used DJCJ Arcade before libraries existed, everything you had is now your first
library, called Default, exactly where it always was. Nothing was moved or copied.

The **Libraries** window lists every library, with the emulator version each one's catalog
was built from. Open it from **DJCJ Arcade → Switch Library…**, from the library strip at
the bottom of the sidebar, or by holding **Option** while DJCJ Arcade opens. Choose a
library to open it, and DJCJ Arcade restarts into it. If the library DJCJ Arcade last had
open can't be found, say because it's on a drive that isn't connected, the Libraries window
opens instead, rather than quietly opening a different one.

**New Library…** asks for a name, where to put the library's folder, and which emulator it
uses: MAME or HBMAME from Homebrew, each with an Install button if you don't have it yet,
or **I'll choose one later**. A new library starts empty and opens right away, and its
Setup Wizard takes it from there. Nothing is copied from another library.

**Open Existing…** adds a library folder that isn't in your list yet, such as one you made
on another Mac. Each library folder holds everything that library needs, its settings
included, so you can move it, copy it to another Mac, or keep it on an external drive.
The one exception is the original Default library from before libraries existed, which
keeps its files where they always were; Convert to Library Folder, below, gives it a
folder of its own.

Under **More**, for whichever library is selected:

- **Rename…** changes its name.
- **Show in Finder** shows its folder.
- **Remove from List** takes it out of the list without touching its folder, so you can
  add it back later with Open Existing.
- **Move to Trash…** moves its folder to the Trash after asking first, so you can still
  put it back until you empty the Trash. If the library's Working Folder is somewhere
  outside its folder, that stays where it is, and the confirmation says so. This isn't
  offered for the library that's open, or for the original Default.
- **Convert to Library Folder…**, for the original Default library, copies it into a folder
  of its own, so it can be moved or copied like any other library, then opens that copy.
  The original stays where it is, and in the list, until you remove it.

A few things belong to DJCJ Arcade as a whole rather than to any one library, like its
appearance and the Log. Each Log entry says which library it came from.

## Browsing, sorting, and filtering

Click any column header to sort by it, and you can add a second sort underneath the
first, so you might sort by manufacturer and then by year within each manufacturer. The
Filter menu narrows the list down: hide clones, hide machines with an imperfect driver,
hide mechanical machines, hide BIOS sets (the system firmware that groups of machines
share), and so on. Filtering never permanently removes anything from
the catalog. It's about what's showing right now, not what exists.

Drag a column header to move that column, or drag its edge to make it wider or narrower.
To choose which columns show at all, right-click any column header and tick or untick
them, or use View → Machine List Columns (and View → Software List Columns for a software
list). A column you hide comes back exactly where it was when you show it again, and
Restore Default Columns in either menu puts every column back the way it started. The Name
column always stays, so you can always tell which machine is which.

Machines that are really a whole platform rather than one single game, an Atari 2600 or
a Game Boy for instance, can be opened up to show everything that runs on them. Double
click in, or use the arrow next to its name, and you get that platform's own software
list instead of one line in the machine table.

The search box, just above the list, finds things by name across the whole catalog.
Command F jumps straight to it.

## Knowing what you actually have

The catalog describes everything MAME supports, which is not the same as everything you
own. Every machine and title has a **Have** column, and a filter that shows only the
things you can actually play right now.

To fill that column in, MAME needs to check your files against what it expects for each
machine, which the app calls an audit. **DJCJ Arcade → Audit Machines** and **DJCJ Arcade →
Audit Software Collection** are two separate operations, run separately, because auditing
software takes a good deal longer than auditing machines and not everyone wants to pay
that cost every time. For any single machine or software title, its own details channel
shows you exactly which files it needs, which ones were found, where each one was found,
and whether MAME itself considers the result good. The Setup Wizard's Check What You Have
step runs both audits for you, one after the other.

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

To add something to a collection, drag it onto the collection in the sidebar, or
right-click it and choose from the collections listed there. **Machine → Add to
Collection** does the same from the menu bar. Both lists are laid out like the sidebar,
with each folder as a heading and its collections indented beneath it.

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

Software titles have the same checklist on their own **Software Details** channel: every
file the title needs, across every disk or cartridge it came on, whether each one was
found, and MAME's verdict on it. Check ROMs there only checks that one title, so it takes
a second or two rather than auditing the whole software list it belongs to.

Every row in the checklist, for machines and software alike, has a **Reveal in Finder**
button that shows you the file, or the archive it's inside, in the Finder. Hold the
pointer over it to see which archive that is. When a file wasn't found, the button is
there but greyed out, so the rows stay lined up.

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
With [RetroArch support](#launching-in-retroarch) turned on, the Launch area has a MAME
tab and a RetroArch tab, and Launch runs whichever one is showing.

Next to the Launch button is a row of checkboxes and dropdowns, described fully in the
next section. What you see there depends entirely on what you've set up in Settings →
Launch Decisions, which starts out with a handful of common ones already in place and
grows however you want from there.

If you select a machine that has more than one disk drive, like an old home computer
with a floppy drive or two and maybe a hard disk, you can save a
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

A new install starts with seven, as examples of what's possible as much as anything,
and you can change or delete any of them:

- **Antialiased Resizing**, off. Smooths the picture when MAME scales it up.
- **Fullscreen**, off. Runs MAME full screen rather than in a window.
- **Maximize**, on. Opens MAME's window as large as your screen allows.
- **Uneven Stretch**, on. Lets the picture stretch to fill the window rather than keeping
  to whole-number multiples of its original size. It writes `-unevenstretch` when ticked
  and `-nounevenstretch` when not.
- **Art**, a Dropdown offering Full Art, Overlay Only (the starting choice), No Art, and
  Defer to ini, which leaves the question to whatever your regular settings already say.
- **CRT Shader**, off. Draws the picture the way an old tube screen would, scanlines and
  all.
- **Enable Cheats**, off. Turns on MAME's cheat menu, using the `cheat.7z` file from your
  EXTRAs pack. Without an EXTRAs pack, MAME simply has no cheats to offer.

If you started using DJCJ Arcade before these defaults existed, you keep whatever you
already had, and nothing is added behind your back.

While you're editing one of these, a row of buttons above the list, things like ROMs,
Working Folder, Artwork Path, and Config Directory, let you click a real path into your
command text instead of typing it out and risking a typo. Reorder decisions with the
arrows, which matters beyond just how they're displayed: this is the actual order their
text gets added to MAME's command line, so if two enabled decisions ever write the same
option, whichever one is lower in the list wins.

Turning off a decision's **Ask at launch** checkbox removes it from the footer entirely,
for both the ticked and unticked text, and lets MAME's own settings files decide that
question on their own instead.

## MAME Launch Codes

This channel was called Launch Codes before RetroArch got one of its own.

MAME reads its settings from several files, in a fixed order, and each one can override
whatever came before it: one file for everything, then one for every machine sharing a
particular kind of screen, then one for everything sharing a chipset, and finally one for
the single machine you're looking at. It's a genuinely powerful system, and it's also
easy to lose track of, since the setting you're hunting for could be sitting in any one
of those files, and something further down the chain might be quietly overriding it
without telling you.

**MAME Launch Codes** is a channel that lays this whole chain out for whichever machine
is selected, in order, color coded, and tells you plainly which files are actually active
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

## Launching in RetroArch

If you also use [RetroArch](https://www.retroarch.com), DJCJ Arcade can launch machines and
software titles in it instead of MAME. It's off until you turn on **Enable RetroArch
support** in Settings → RetroArch. RetroArch has to be set up already with the cores you
want, and DJCJ Arcade never changes any of RetroArch's own settings.

### Setting it up

In Settings → RetroArch:

- **RetroArch App** is where RetroArch is. **Choose…** picks it.
- **Remember MAME or RetroArch for each machine**, when it's on, switches the Launch area
  to the tab and core you last used for each machine whenever you select it. When it's
  off, the tab stays wherever you left it.
- **Cores** is the list of choices in the RetroArch tab's core menu, in this order. Drag to
  reorder them, **Add** your own, or change one if RetroArch renames a core. It starts
  with Arcade (MAME), FinalBurn Neo, MAME 2016, and MAME 2003-Plus.

Each core has:

- **Name**, what the core menu shows.
- **Core**, the name RetroArch knows it by. That can be its short name, like `mame`, its
  file name, or a full path to it.
- **Launch With**, which is how DJCJ Arcade hands it a game. **MAME command file** is for
  MAME's own cores: DJCJ Arcade writes a small file naming the exact machine and every ROM
  folder you've set in Settings, so clones from a merged set, machines whose CHDs live in a
  separate folder, and software lists all work. **ROM file** is for cores that only read a
  single zip, like FinalBurn Neo. That's best effort: a clone in a merged set has no zip of
  its own to hand over.
- **ROM Folder**, optional, for a ROM set made for that core, like an FBNeo set. Left
  blank, the core gets the ROM folders from Settings.
- **Extra Arguments**, optional, added to RetroArch's command line as written. A
  `--set-shader` here turns shaders on for that launch even if they're off in RetroArch.

Like the rest of a library's settings, all of this belongs to the library that's open.

### Launching

With RetroArch support on, the Launch area has **MAME** and **RetroArch** tabs, and the
Launch button says which one it will use: **Launch with MAME** or **Launch with
RetroArch**. On the RetroArch tab, a **Core** menu picks which core runs the game, and a
**Version** menu picks between the machine itself and any variants, described below. You can also skip the tabs: right-click a machine or title, or use the Machine
menu, and choose **Launch with MAME** (Option Command L) or **Launch with RetroArch**
(Control Command L).

Games launched from DJCJ Arcade don't start paused. RetroArch normally pauses a game
while it isn't the app in front, and when another app starts it, it can begin that way.
DJCJ Arcade turns that off for its own launches only, without changing your RetroArch
settings.

If a launch fails, the message leads with RetroArch's own errors rather than its routine
warnings, and offers **Switch to MAME**.

Check ROMs uses the MAME installed on your Mac, so it doesn't tell you whether a RetroArch
core has what it needs. Cores like FinalBurn Neo or MAME 2003-Plus may want ROM sets of
their own.

### Variants

Some cores have hacks and other versions of a machine that MAME itself doesn't, such as
1942c64 under 1942. A variant launches one of those in the original's place. Add them on
the RetroArch Launch Codes channel with **Add Variant**: for a machine, type to search your
cores' own game lists, the ones RetroArch provides, or use **Add by Hand**. For a software
title, choose the file to use instead, which is how you'd add something like a fan
translation.

Each variant has a name and a core, which is either a specific core or **The Launch area's
core**. The RetroArch tab's **Version** menu, beside the Core menu, lists **Original** for
the machine itself, then its variants, then **Edit Variants…**, which takes you to the
RetroArch Launch Codes channel. A variant set to a specific core takes the Core menu over
while it's chosen.

### RetroArch Launch Codes

The RetroArch counterpart to MAME Launch Codes, a channel showing exactly what Launch with
RetroArch will run for the selected machine or title:

- **Game File**, the command file or ROM file DJCJ Arcade hands the core. A command file is
  written fresh from your ROM folders each time you launch.
- The settings applied on top of RetroArch's own, for that launch only: the setting that
  keeps games from starting paused, shaders when a core's extra arguments choose one, and
  a setting that stops RetroArch saving any of this into its own configuration.
- **Command Line**, the full command. **Copy** also writes the files it uses, so you can
  paste it into Terminal and run it yourself, even for something you've never launched
  from DJCJ Arcade.
- **Variants**, described above.

When the Launch area is set to MAME, this channel says its codes aren't being used right
now, and MAME Launch Codes does the same when it's set to RetroArch.

## Other things on the Machine menu

**Launch with MAME** (Option Command L) and **Launch with RetroArch** (Control Command L)
are here while RetroArch support is turned on.

**Copy Command Line** (Shift Command C) copies the exact command that would run if you
launched right now, including every setting from every layer of the chain and any Launch
Decisions currently ticked. Useful for troubleshooting, or for sharing exactly what you
ran with someone else.

**Download Manual…** (Shift Command D) fetches a manual for the selected machine when
one isn't already sitting in your EXTRAs pack.

**Reveal in Finder** (Shift Command R) shows the selected machine or title's files in the
Finder.

**Check ROMs…** (Option Command V) runs the same file-by-file audit as the Check ROMs
button on Machine Details or Software Details, for whichever machine or software title is
selected, without leaving the list.

## Exporting a collection

Right click any collection, or use the Collections menu, and choose **Export Collection
to Zip…**. This builds one self-contained zip file sized to exactly what that collection
actually needs, rather than pulling in your whole library. It mirrors DJCJ Arcade's own
folder layout, so the result works on its own: a portable ROM set you can hand to a
friend, copy to a Raspberry Pi, or diff against your main library later.

## Verify Database and backups

**DJCJ Arcade → Verify Database…** checks the catalog file itself for the kinds of problem a
bug could theoretically leave behind: broken links between tables, a collection nested
inside itself, a smart collection with rules that no longer make sense, duplicate
collection names, and a few others. Most people will never need this, and it exists so
that if something ever looks wrong, there's a real answer rather than a guess.

**DJCJ Arcade → Back Up or Restore Database…** saves a copy of your whole catalog, your tags,
your collections, your play counts, everything, to a file of your choosing, and can
restore from one later. Worth doing before a big change you're not sure about, or just
now and then for peace of mind.

## Keyboard shortcuts worth knowing

| Shortcut | Does |
| --- | --- |
| Command L | Launch the selected machine or title |
| Option Command L | Launch with MAME, when RetroArch support is on |
| Control Command L | Launch with RetroArch, when RetroArch support is on |
| Command O | Open With, when a title runs on more than one machine |
| Command F | Jump to the search box |
| Command G / Shift Command G | Find Next / Find Previous |
| Command 1 | All Machines |
| Command 2 | Favorites |
| Command ] | Show the selected machine's software |
| Command [ | Back |
| Command Left Arrow / Right Arrow | Previous Channel / Next Channel |
| Shift Command E | Choose which channels are turned on |
| Option Command P | Parents Only |
| Command Comma | Open Settings |
| Shift Command R | Reveal the selected item's files in Finder |
| Shift Command C | Copy Command Line |
| Shift Command D | Download Manual |
| Option Command V | Check ROMs for the selected machine or software title |
| Shift Command A | Audit Machines |
| Option Shift Command A | Audit Software Collection |
| Option Shift Command R | Rebuild Catalog |
| Command R | Refresh EXTRAs Folder Data |
| Shift Command V | Verify Database |
| Shift Command B | Back Up or Restore Database |
| Shift Command N | New Collection |
| Option Command N | New Smart Collection |
| Shift Command L | Show the Log |
| Control Command D | Switch between light and dark |

Full menus have more, this is just the short list of the ones you'll reach for most.

## If something goes wrong

Settings → General lets you turn on a Log of anything unusual MAME reports on launch,
including outright failures, and RetroArch launches that fail too. Each entry says which
library it came from. **Window → Log** shows it, and **Reveal Log in Finder** and
**Clear Log** are right next to it if you need to send someone the actual file or start
fresh.

If you run into a real bug, this repository's Issues page is the place to report it.
