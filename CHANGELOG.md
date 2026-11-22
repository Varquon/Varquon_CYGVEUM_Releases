# Changelog

<!--
  AUDIENCE: end users of the app, NOT maintainers. This file is published as
  the release notes users read. Write only changes a user can SEE or DO
  differently — new/changed/fixed behaviour, features, examples, devices.
  Do NOT mention code internals, refactors, file names, build/CI plumbing,
  API/URL-encoding details, repo structure, or anything invisible in the app.
  Each release adds one "## v<tag> — <date>" section with ### Added / Changed /
  Fixed sub-headings, phrased from the user's point of view.
-->

## v2.0.0 — 2026-11-22
### Fixed
- Clicking a part to select it no longer marks the file as unsaved or adds
  an empty step to Undo. A file now counts as unsaved only when its content
  really changes, and undoing back to the saved state makes it clean again.
- The Inspector on the right no longer cuts off its buttons or scrolls
  sideways when the window or side bar is narrow; buttons wrap onto their own
  rows instead. On a narrow canvas, tools that don't fit move into a **⋯**
  menu at the end of the tool row.

### Changed
- A completely new look, matching varquon.com: warm charcoal and amber, the
  website's typefaces, and a layout that will feel familiar if you use
  VS Code. Everything works the same way; things are just easier to find.
- The window is now organised like VS Code: an activity bar on the left
  switches between **Explorer**, **Components**, **Flow** and **Device**;
  files open in tabs; the Tcl console and output share a panel at the bottom;
  and a coloured status bar shows the flow, the target IC and what the editor
  is doing.
- **Compile** and **Program** now sit at the top right of the window, as
  rounded buttons in the style of varquon.com, with a matching status bar.
- **IC utilization** is always visible at the bottom of the left side bar.
- Schematic parts are drawn as crisp symbols in the theme's colours, and pins
  show their name inside the pin tag.
- Editing tools (wire, parts, rotate, flip, undo, properties…) float above the
  canvas, with a zoom control in the corner.
- Opening a project or folder closes the Welcome page, so you go straight to
  your schematic.

### Added
- Three colour themes — **Ember** (dark, default), **Midnight** (dark) and
  **Paper** (light) — in **File ▸ Preferences ▸ Settings** or with
  Ctrl+K then Ctrl+T. Your choice is remembered.
- A command palette (Ctrl+Shift+P) that runs any command by name, and
  Ctrl+P to jump to any file in the project.
- An **Inspector** on the right showing the selected part's properties and
  connections, with buttons to edit, rotate, flip or delete it.
- A **Welcome** page with recent projects, the example circuits and a
  three-step guide to your first design.
- Text files such as *out.hex*, logs and READMEs open read-only in their own
  tab.
- **File ▸ Open Recent**, and F6 to open the Program stage.
- The window remembers which panels you had open and their sizes.
- Open several schematics and symbols at once, each in its own tab. Click a
  tab to switch, Ctrl+W closes it, and Ctrl+PgUp / Ctrl+PgDown move between
  tabs. Right-click a tab for Close Others, Close Saved and Reveal in
  Explorer. Copied parts can be pasted into another tab.
- **Auto Save**, as in VS Code: in **File ▸ Preferences ▸ Settings ▸ Files**
  choose Off, After a delay, When the editor loses focus, or When the window
  loses focus. **File ▸ Auto Save** turns it on and off quickly.
- CYGVEUM now asks before closing a tab, switching projects or quitting with
  unsaved changes (unless Auto Save is on).
- A **Sources | Output** switch at the top of the Explorer to flip between
  your schematics and symbols and the compile results. An **All** view (every
  project folder) can be turned on in **Settings ▸ Explorer**.
- Opening a schematic or symbol shows the **Components** list in the side
  bar, ready for placing parts (can be turned off in **Settings ▸ Explorer**).
- A **Keyboard Shortcuts** editor (**File ▸ Preferences ▸ Keyboard
  Shortcuts**, F1 or Ctrl+K Ctrl+S): search any command and give it your own
  keys, or remove or reset them. Every part can have its own key too (none by
  default), for example Alt+R to place a resistor. Your keys are remembered.
- The canvas keys (R to rotate, W for wire, X / Y to flip, Esc and so on)
  can be changed in Keyboard Shortcuts too.
- Double-click a part on the canvas to edit its properties.
- Right-click in the Explorer for **New Schematic…** and **New Symbol…**
  (on the folders, on files inside them, or on empty space).
- A symbols button (chip icon) on the canvas tool row lists the project's
  symbols: pick one and click to place it. Symbols are also first in the Components
  view, and right-clicking a symbol file offers **Place in Schematic**.
- IC utilization turns red only when you place more of a part than the IC
  has. Parts the IC doesn't have at all (for example a capacitor) appear in
  red, marked "not on this IC".
- Battery and LED are no longer offered in the Components list (schematics
  that already use them still open).
- A much more capable **Tcl console**. It runs real Tcl, so variables, loops,
  `proc`, `if` and `catch` all work, and it has over 50 commands to drive the
  app, including editing the schematic in the style of Magic: `place`, `move`,
  `rotate`, `flip`, `delete`, `rename_part`, `value`, `setprop`, `wire`,
  `connect`, `select`, `fit`, `zoom`, plus project and flow commands such as
  `open_project`, `open_file`, `compile`, `program`, `utilization` and `save`.
  Everything one console line (or one script) changes is a single Undo step.
- Run a Tcl script with `source <file.tcl>` in the console, or with
  **Tools ▸ Run Tcl Script…**.
- **Help ▸ Console Commands** lists every console command with its usage, a
  description and an example; search it and click **Put in console** to try
  one. `help <command>` in the console shows the same details.

## v1.2.3 — 2026-06-04
### Changed
- The example projects and device library are now installed into your
  Documents folder (under *Varquon CYGVEUM*) the first time you run the app,
  instead of being loaded from a temporary location. Installing a newer version
  of the app refreshes them to that version's set.

### Added
- A setup window now appears while the examples and device library are being
  installed, and progress windows are shown while they load or update, so you
  can always see what the app is doing instead of it appearing to wait.

## v1.2.2 — 2026-06-04
### Fixed
- "Update Device Library + Examples" now works for every example, including
  ones whose names contain spaces (such as *Common-Source Amplifier*), which
  previously failed to download.

### Added
- While an update runs, a window now shows its progress and what is currently
  being downloaded, so it is clear the app is working rather than frozen.

## v1.2.1 — 2026-06-04
### Added
- Four new example projects, each with its core circuit as an importable
  symbol: Resistance Divider, RC Filter (capacitor off-chip via external
  pins), MOSFET Switch, and Common-Source Amplifier.

### Changed
- The blank `project_example` moved out of the bundled examples (it is a
  developer template, no longer copied into users' example list).

## v1.2.0 — 2026-06-04
### Added
- Symbol pins can now be named freely, and the name is drawn on the symbol
  box. Each pin's position is set with an explicit **Side** (top/bottom/left/
  right) and **Order**, replacing the old `p1_1` / `p2` naming scheme.
- Top-level schematic pins choose their IC external bond from a dropdown
  (`ext_000`…), which hides any external already claimed by another pin.
- Examples can be imported as symbols into the current project (auto-renaming
  on name clashes), in addition to opening one as a brand-new project.
- This CHANGELOG, mirrored into the releases repo and used as the release
  notes for each tag.

### Fixed
- Two symbol pins can no longer share the same name, or the same Side + Order.
- macOS build: skip the unsupported PyInstaller splash screen and convert the
  app icon to `.icns` via Pillow.

---

## v1.1.0 — 2026-06-03
- Rebrand to Varquon **CYGVEUM**; projects use the `.cyv` extension; first-run
  splash screen and app icon.
