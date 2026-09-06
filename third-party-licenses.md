# Third-party components

Components DJCJ Arcade links against, and what each one's license requires of us. This file
exists to satisfy those requirements, so it needs to ship with the app rather than only live
in the repository.

## FFmpeg (libavcodec, libavformat, libavutil, libswscale, and friends)

DJCJ Arcade uses libraries from the **FFmpeg** project, licensed under the
**GNU Lesser General Public License version 2.1 or later (LGPL-2.1-or-later)**.

- FFmpeg project: <https://ffmpeg.org>
- FFmpeg source: <https://github.com/FFmpeg/FFmpeg>
- The prebuilt Apple-platform binaries come from **FFmpegBuild**, which also documents how
  they were configured and built: <https://github.com/superuser404notfound/FFmpegBuild>
- LGPL-2.1 text: <https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html>

FFmpeg is **dynamically linked**, as embedded `.framework` bundles inside the app. That is
what keeps DJCJ Arcade's own code separable from it, and it is what lets a user replace the
FFmpeg libraries with their own build if they wish, which is the freedom LGPL section 6 is
there to protect.

Only the *decoder* is used, and only for one specific job: the video snaps in the
third-party media packs are H.264 High 4:4:4 Predictive, which macOS cannot decode by any
native route. Encoding, playback, audio, and everything else are Apple's own frameworks.
No GPL-licensed FFmpeg components (x264, x265, and similar) are included, which is what keeps
this LGPL rather than GPL.

## ZIPFoundation

MIT licensed. <https://github.com/weichsel/ZIPFoundation>

Used to write the zip file behind Export Collection to Zip.

## GRDB.swift

MIT licensed. <https://github.com/groue/GRDB.swift>
