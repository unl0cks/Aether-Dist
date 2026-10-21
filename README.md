<div align="center">

<img src="https://raw.githubusercontent.com/unl0cks/Aether-Dist/main/assets/aether-icon.png" alt="Aether" width="280">

# Aether

**A desktop client for AdventureQuest Worlds, built on Ruffle.**

Flash is gone and the game is not. Aether runs AQW natively on Windows, macOS and Linux, without a
browser and without a plugin, and spends most of its effort on the parts of the game that a general purpose
Flash player has no reason to care about: how smooth it looks, how fast it draws, and how the game's
own interface feels to use.

**Aether is exclusive to the Vibes guild.** Whisper Rab or an officer in game for an invite.

[![Latest release](https://img.shields.io/github/v/release/unl0cks/Aether-Dist?label=release&color=2f81f7)](https://github.com/unl0cks/Aether-Dist/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/unl0cks/Aether-Dist/total?color=2f81f7)](https://github.com/unl0cks/Aether-Dist/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-2f81f7)](https://github.com/unl0cks/Aether-Dist/releases/latest)
[![AQW](https://img.shields.io/badge/AQW%20client-5.0-2f81f7)](https://github.com/unl0cks/Aether-Dist/releases/latest)

[**Download**](https://github.com/unl0cks/Aether-Dist/releases/latest) &nbsp;·&nbsp;
[What's in it](#whats-in-it) &nbsp;·&nbsp;
[Aether Options](#aether-options) &nbsp;·&nbsp;
[Privacy](#privacy) &nbsp;·&nbsp;
[Terms of use](https://github.com/unl0cks/Aether-Dist/blob/main/TERMS.md) &nbsp;·&nbsp;
[Antivirus warnings](#if-your-antivirus-flags-the-download) &nbsp;·&nbsp;
[Reporting a problem](#reporting-a-problem)

</div>

---

> [!TIP]
> Almost everything Aether adds can be switched on or off, and most of it adjusted, in **Aether
> Options**. Press **F1** in game, or click the Aether button on your portrait.

## Install

Everything is on the [releases page](https://github.com/unl0cks/Aether-Dist/releases/latest). Once
Aether is installed it looks for new versions by itself and asks you before installing one, so you only
ever download by hand once.

By installing or using Aether you agree to the
[terms of use](https://github.com/unl0cks/Aether-Dist/blob/main/TERMS.md). The Windows installer shows
them before it installs anything, and every download carries them as `TERMS.md`.

### Windows

| | |
| :-- | :-- |
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

Cmd+, opens Aether Options, as it does in any Mac application.

### Linux

**`Aether-<version>-linux-x64.tar.gz`**, for 64 bit Intel and AMD machines with glibc 2.31 or later
(Ubuntu 20.04, Debian 11, Fedora 32 and anything newer), and a Vulkan driver. Unpack it and run:

```sh
./install.sh
```

That puts Aether in `~/.local/opt/aether` with an entry in your applications menu, and needs no
root. `./install.sh --uninstall` removes it again and keeps your settings. You can also run `./aether`
straight from the unpacked folder without installing.

### Checking a download

Every release also carries `SHA256SUMS.txt`, signed as `SHA256SUMS.txt.sig`. To check that the file
you have is the file that was published, compare its hash with its line there:

```powershell
Get-FileHash .\Aether-Portable-X.X.X-win-x64.zip -Algorithm SHA256
```

(Replace `X.X.X` with the version number. On macOS and Linux, `shasum -a 256 <file>` or
`sha256sum <file>` does the same.)

## Updates

Aether looks for a new version each time it starts. When there is one, a small window opens over the
game once Aether is up, says which version you have and which is out, and asks whether to update now.
**Update now** downloads and installs it and restarts into the new version; **Not now** leaves
everything as it is and asks again next time; **Open changelog** shows what changed. The same window
opens from **Check for updates** on the About tab of Aether Options. It works the same way on Windows, macOS and Linux.

Every release is signed, and Aether checks that signature before anything is put in place, so an
update that did not come from here is refused.

## What's in it

### AQW client 5.0

Aether logs in and works with AQW's new 5.0 client, and its inventory tools know the new windows:
item types as tabs, categories down the side, a sorting header, enhancements and boosts on every row,
favourites, and a preview of the item on your own character in the inventory, shops, merge shops, the
bank, and the windows drops and quest rewards open.

**Legacy UI** brings back the inventory, shop, merge shop and bank windows the game had before 5.0,
for anyone who prefers them.

### Looks and feel

- **Smooth animation.** Characters and monsters are drawn between their animation frames, so movement
  is smooth at any frame rate while still playing at the speed AQW intends. Every character keeps its
  own timing, and walking no longer stutters where its loop starts over.
- **Press feedback.** Buttons sink a little while you hold them, and the number keys 1 to 6 press
  their skills the same way. A skill that cannot be used right now flashes red instead.
- **Smooth, rounded bars.** The portrait bars slide to their new values instead of jumping, and can be
  drawn rounded in the game's own colours. The bar over everyone's name is health over mana on a small
  plate, with its own size, thickness and roundness.
- **Aura displays your way.** How many to a row, how big, how far apart, grouped by who cast them,
  pinned so they never move by accident, or following the character around and staying clear of the
  damage numbers.
- **Redrawn skill icons** for older classes, with a choice of drawings per class.
- **Living shadow**, cast by your character or by everyone, moving as they move.
- **Smooth scrolling**, a font you can read for chat, nameplates or the whole interface, number
  grouping, tooltips that follow the pointer, movable combat messages, alerts and screen-edge
  vignettes, and a frame counter you can put where you want it.

### Living with the game

- **Animation at the speed it was drawn.** AQW's frame rate setting also sets how fast everything
  animates, so at 60 everything plays two and a half times too fast. Aether holds animation, combat
  messages, drop notes, the skill bar and loading screens at their intended speed while still drawing
  at the full rate.
- **A pet that no longer overtakes you.** AQW measures a pet's walk in frames and yours by the clock,
  so above about 35 frames a second the pet arrives first. You can also choose how far it follows.
- **A faster inventory**, which opens long lists noticeably quicker.

### Speed

AQW draws in a way that is expensive for a general purpose renderer, and most of Aether's rendering
changes are about spending less to draw the same picture. Among them:

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

## Aether Options

Press **F1** in game (the binding is yours to change), click the Aether button on your portrait, or
press Cmd+, on a Mac. The window reopens on the tab and spot you left it at.

| Tab | What lives there |
| :-- | :-- |
| **Gameplay** | Skills and auras, damage numbers, number grouping, tooltips, alerts |
| **Redrawn Class Options** | Redrawn skill icons for older classes |
| **Game Interface** | Legacy UI and the inventory, bank and shop tools, windows, scrolling, fonts, smooth animation and movement, bars, shadows, combat messages |
| **Visuals & Performance** | Quality, antialiasing, frame rate, video memory, the key that opens this window |
| **Quality of Life** | Interface size, the frame counter |
| **Advanced** | Caching, texture memory, crash reports, compatibility repairs |
| **Experimental & Debugging** | The rendering changes above, each with what it was measured to be worth and what a fault would look like |
| **About** | The version you have, and Check for updates |

Most settings apply the moment you save. The window says so when one needs a restart.

## Privacy

> [!IMPORTANT]
> **Aether reads nothing about your computer to identify it:** no hardware identifiers, no machine ID
> or GUID, no computer name and no user name.

To check guild membership, Aether sends the developer's membership server your AdventureQuest Worlds
account name, a random identifier that your copy of Aether made up for itself the first time it ran,
and the version you are running. The server reads the guild on your public AQW character page. It keeps
your account name, a scrambled (salted hash) form of the random identifier, and when that copy last
checked in. It does not keep your network address, and it throws away any raw identifier it is sent.

Aether also asks GitHub whether a newer version exists, and the game talks to Artix Entertainment's
servers exactly as it would in a browser. Logs and crash reports stay on your computer unless you
choose to send them, and never contain your user name. The
[terms of use](https://github.com/unl0cks/Aether-Dist/blob/main/TERMS.md) say the same in full.

## If your antivirus flags the download

**It is a false positive, and you can verify that yourself rather than taking our word for it.**

Aether is not code signed. A signing certificate has to be bought and renewed, and until there is
one, every release is a file Windows has never seen before, published by nobody it recognises. On
top of that Aether does two things that look exactly like the things malware does: the installer
carries a compressed payload that it unpacks and runs, and the client downloads a new copy of itself
when it updates. Those are an installer and an updater doing their jobs, and no heuristic scanner
can tell them apart from the alternative.

What to do:

1. **Check the hash** against `SHA256SUMS.txt` on the release, as [above](#checking-a-download). If
   it matches, the file is the one that was published and nothing has tampered with it in transit.
2. **Upload it to [VirusTotal](https://www.virustotal.com/)** if you want a second opinion. Expect a
   small number of engines to object and the majority not to.
3. **Restore it rather than downloading again.** If Windows Defender has already quarantined the
   file, it is still on your machine. Windows Security, then Protection history, then find the item
   and choose Restore. Downloading a second copy will usually just be blocked a second time.
4. **Some chat clients block it too.** Discord scans attachments and will refuse the zip once it has
   decided it does not like it. Download from the releases page instead, which is a different path
   and is not affected.

## Command line

Aether needs no arguments. Launched with none it opens the live AQW loader and applies the AQW
preset. A few flags are worth knowing about:

| Flag | Effect |
| :-- | :-- |
| `--generic` | Behave as ordinary Ruffle and skip the AQW preset entirely |
| `--maxfps <n>` | The rate the game is run at. Read the tooltip on the matching setting first, because this is not a limit on drawing |
| `--msaa1x`, `--msaa2x`, `--msaa4x` | Pin antialiasing rather than letting Aether choose |
| `--low-vram` | A much smaller texture budget, for cards that cannot spare the default |
| `--ui-font <family>` | The interface font, same as the setting |
| `--metrics` | Write one second performance summaries as JSON Lines, for diagnosing a report |

`aether --help` lists the rest. Passing an SWF path or URL also keeps Aether in generic mode.

## Reporting a problem

AQW changes constantly and some of it lands before anyone has run it here. Reports are useful.

**For a visual or gameplay fault**, say which map, roughly how many other players were on screen,
what you were wearing or had shown, and what you did. Gear matters more than it sounds: several
faults have turned out to be one item.

**For a crash or a slowdown**, send the log folder. It is at:

| | |
| :-- | :-- |
| Windows | `%LOCALAPPDATA%\aether\log` |
| macOS | `~/Library/Caches/aether/log` |
| Linux | `~/.cache/aether/log` |

That holds `ruffle.log` and, if Aether has died, a file named `aether-crash-` and a timestamp. The
crash report carries your graphics adapter, the settings actually in force, and the last few hundred
lines before the fault, which together answer most questions in one go.

**If Aether keeps crashing on integrated graphics**, there is something to try first. Set the
environment variable `AETHER_MAX_PASSES_PER_SUBMISSION` to `16` and play as normal. It hands the
graphics driver smaller batches of work, which costs roughly a fifth of your frame rate and holds
eight times fewer driver allocations open at once. If that stops the crashes, say so, because it
turns a workaround into something that can be fixed properly.

## Building from source

This part is for the source repository. Install a current Rust toolchain, then:

```powershell
.\scripts\check-aether.ps1
.\scripts\build-aether-windows.ps1
```

The optimized executable is written to `target\dist\aether.exe`. To build what a release actually
ships, the installer and the portable zip together:

```powershell
pwsh .\installer\build-setup.ps1
```

Both land in `installer\dist`. Use `pwsh` rather than Windows PowerShell 5.1 for that one; the
script relies on escapes 5.1 does not understand and will otherwise fail quietly.

The Linux client is cross-built on Windows with zig and cargo-zigbuild, and the macOS client on
GitHub's macOS runner, since Apple's SDK may only be used on Apple hardware:

```powershell
pwsh .\installer\build-linux.ps1
pwsh .\installer\fetch-macos.ps1 -Start
```

The notes at the top of each script say what they need.

## Licensing and attribution

Aether is derived from [Ruffle](https://ruffle.rs), and keeps the licensing and attribution
obligations of that base and of every dependency it carries. Those licences come with every download,
in `LICENSE.md` and `THIRD-PARTY-NOTICES.md`.

AdventureQuest Worlds is a trademark of Artix Entertainment. Aether is an unofficial client, is not
affiliated with or endorsed by Artix Entertainment, and ships none of the game's content: it loads
the same files from the same servers a browser would.
