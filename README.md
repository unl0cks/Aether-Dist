<div align="center">

<img src="https://raw.githubusercontent.com/unl0cks/Aether/main/aether/assets/aether-icon.png" alt="Aether" width="280">

# Aether

**A desktop client for AdventureQuest Worlds, built on Ruffle.**

Flash is gone and the game is not. Aether runs AQW natively on Windows, macOS and Linux, without a
browser and without a plugin, and spends most of its effort on the parts of the game that a general purpose
Flash player has no reason to care about.

**Aether is exclusive to the Vibes guild.** Whisper Rab or an officer in game for an invite.

[![Latest release](https://img.shields.io/github/v/release/unl0cks/Aether-Dist?label=release&color=2f81f7)](https://github.com/unl0cks/Aether-Dist/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/unl0cks/Aether-Dist/total?color=2f81f7)](https://github.com/unl0cks/Aether-Dist/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-2f81f7)](https://github.com/unl0cks/Aether-Dist/releases/latest)

[**Download**](https://github.com/unl0cks/Aether-Dist/releases/latest) &nbsp;·&nbsp;
[Terms of use](TERMS.md) &nbsp;·&nbsp;
[Privacy](#privacy) &nbsp;·&nbsp;
[Antivirus warnings](#if-your-antivirus-flags-the-download) &nbsp;·&nbsp;
[Reporting a problem](#reporting-a-problem)

</div>

---

## Install

Everything is on the [releases page](https://github.com/unl0cks/Aether-Dist/releases/latest). Once
Aether is installed it looks for new versions by itself and asks you before installing one, so you only
ever download by hand once.

By installing or using Aether you agree to the [terms of use](TERMS.md). The Windows installer shows
them before it installs anything.

### Windows

| | |
|---|---|
| **`Aether-Setup-<version>-win-x64.exe`** | The installer. Creates shortcuts, registers an uninstaller, and is the one to take if you have no reason to prefer the other. |
| **`Aether-Portable-<version>-win-x64.zip`** | Unzip it anywhere and run `aether.exe`. Nothing is written outside the folder except your settings and logs. |

Windows 10 or 11, 64 bit.

### macOS

**`Aether-<version>-macos-universal.dmg`**, for Apple silicon and Intel Macs on macOS 11 or later.
Open it and drag Aether onto the Applications folder beside it.

Aether is not signed with an Apple developer account, so the first time you open it macOS will say
it cannot check it. Right-click Aether in Applications, choose Open, then Open again. On macOS 15
and later there may be no Open button: try to open it once, then go to System Settings, Privacy &
Security, and choose Open Anyway. This is only needed once.

The `.zip` beside it holds the same app with an `Install Aether.command` that does the copying and
the first-open step for you.

Cmd+, opens the options window, as it does in any Mac application. On a Mac, new versions are
installed from the options window's Check for updates button.

### Linux

**`Aether-<version>-linux-x64.tar.gz`**, for 64 bit Intel and AMD machines with glibc 2.30 or later
(Ubuntu 20.04, Debian 11, Fedora 32 and anything newer), and a Vulkan driver. Unpack it and run:

```sh
./install.sh
```

That puts Aether in `~/.local/opt/aether` with an entry in your applications menu, and needs no
root. `./install.sh --uninstall` removes it again and keeps your settings. You can also run `./aether`
straight from the unpacked folder without installing.

### Checking a download

Every release also carries `SHA256SUMS.txt`. If you want to check that the file you have is the file
that was published, compare it:

```powershell
Get-FileHash .\Aether-Portable-X.X.X-win-x64.zip -Algorithm SHA256
```

(Replace `X.X.X` with the version number. On macOS and Linux, `shasum -a 256 <file>` or
`sha256sum <file>` does the same.)

## Updates

Aether looks for a new version each time it starts. When there is one it tells you which version you
have and which is available, and asks whether to update now. Say no and Aether starts as it is and asks
again next time. Every release is signed, and the signature is checked before anything is downloaded
into place, so an update that did not come from here is refused.

## Privacy

Aether reads nothing about your computer to identify it: no hardware identifiers, no Windows machine
ID, no computer name and no user name.

To check guild membership, Aether sends the developer's membership server your AdventureQuest Worlds
account name, a random identifier that your copy of Aether made up for itself the first time it ran,
and the version you are running. The server reads the guild on your public AQW character page. It keeps
your account name, a scrambled (hashed) form of the random identifier, and when that copy last checked
in. It does not keep your network address.

Aether also asks GitHub whether a newer version exists, and the game talks to Artix Entertainment's
servers exactly as it would in a browser. Logs and crash reports stay on your computer unless you
choose to send them. The [terms of use](TERMS.md) say the same in full.

## If your antivirus flags the download

**It is a false positive, and you can verify that yourself rather than taking our word for it.**

Aether is not code signed. A signing certificate has to be bought and renewed, and until there is
one, every release is a file Windows has never seen before, published by nobody it recognises. On
top of that Aether does two things that look exactly like the things malware does: the installer
carries a compressed payload that it unpacks and runs, and the client downloads a new copy of itself
when it updates. Those are an installer and an updater doing their jobs, and no heuristic scanner
can tell them apart from the alternative.

What to do:

1. **Check the hash** against `SHA256SUMS.txt` on the release, with the command above. If it matches,
   the file is the one that was published and nothing has tampered with it in transit.
2. **Upload it to [VirusTotal](https://www.virustotal.com/)** if you want a second opinion. Expect a
   small number of engines to object and the majority not to.
3. **Restore it rather than downloading again.** If Windows Defender has already quarantined the
   file, it is still on your machine. Windows Security, then Protection history, then find the item
   and choose Restore. Downloading a second copy will usually just be blocked a second time.
4. **Some chat clients block it too.** Discord scans attachments and will refuse the zip once it has
   decided it does not like it. Download from the releases page instead, which is a different path
   and is not affected.

## What Aether does differently

It is not just Ruffle pointed at the game. The work splits into two halves.

### Speed

AQW draws in a way that is expensive for a general purpose renderer, and most of Aether's changes
are about spending less to draw the same picture. Among them:

- Objects that share a glow are blurred together in one pass instead of one pass each, gathered
  together first so that more of them qualify.
- Multiply layers over a solid backdrop are handed to the graphics card as it draws, instead of
  costing a separate copy of the screen.
- Effects that read the screen underneath them are given only the part they actually read, instead
  of a copy of the whole thing.
- Colour adjustments ride along with the drawing rather than taking a surface of their own.
- The search for what is under your mouse pointer is skipped on frames where the pointer has not
  moved.

Every one of these is measured rather than assumed, and every one can be switched off if it ever
misbehaves.

### Living with the game

- **A pet that no longer overtakes you.** AQW measures a pet's walk in frames and yours by the
  clock, so above about 35 frames a second the pet arrives first.
- **Animation at the speed it was drawn.** The frame rate setting replaces the speed the game runs
  at, so at 60 everything animates two and a half times faster than intended. This can be held back
  without making anything else choppy.
- **A font you can read**, applied to chat and nameplates or to the whole interface.
- **Smooth scrolling**, number grouping, tooltips that follow the pointer, a recolourable Focus aura,
  item previews on your own avatar, and a frame counter you can put where you want it.

## The options window

Press **F1** in game. The binding is yours to change.

| Tab | What lives there |
|---|---|
| **Gameplay** | Skills, number grouping, damage numbers, tooltips, alerts |
| **Redrawn Class Options** | Skill icons redrawn for older classes |
| **Game Interface** | Inventory, bank and shop tools, window animations, scrolling, fonts |
| **Visuals & Performance** | Quality, antialiasing, frame rate, video memory |
| **Quality of Life** | Interface, movement, the frame counter |
| **Advanced** | Caching, texture memory, crash reports, compatibility repairs |
| **Experimental & Debugging** | The rendering changes above, each with what it was measured to be worth and what a fault would look like |

Most settings apply the moment you save. The window says so when one needs a restart.

## Reporting a problem

AQW changes constantly and some of it lands before anyone has run it here. Reports are useful.

**For a visual or gameplay fault**, say which map, roughly how many other players were on screen,
what you were wearing or had shown, and what you did. Gear matters more than it sounds: several
faults have turned out to be one item.

**For a crash or a slowdown**, send the log folder. It is at:

| | |
|---|---|
| Windows | `%LOCALAPPDATA%\aether\log` |
| macOS | `~/Library/Caches/aether/log` |
| Linux | `~/.cache/aether/log` |

That holds `ruffle.log` and, if Aether has died, a file named `aether-crash-` and a timestamp. The
crash report carries your graphics adapter, the settings actually in force, and the last few hundred
lines before the fault, which together answer most questions in one go.

## Licensing and attribution

Aether is derived from [Ruffle](https://ruffle.rs), and keeps the licensing and attribution
obligations of that base and of every dependency it carries. The source and its licences are at
[unl0cks/Aether](https://github.com/unl0cks/Aether).

AdventureQuest Worlds is a trademark of Artix Entertainment. Aether is an unofficial client, is not
affiliated with or endorsed by Artix Entertainment, and ships none of the game's content: it loads
the same files from the same servers a browser would.
