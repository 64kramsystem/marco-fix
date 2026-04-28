## Marco (fix fork)

This is a fix fork of MATE Marco carrying a single patch on top of upstream tag `v1.26.2`:

- **`window: focus modal dialogs whose ancestor is the focused window`** — fixes [issue #784](https://github.com/mate-desktop/marco/issues/784): modal dialogs (e.g. VS Code's "Save As", any GTK file-chooser opened from an Electron app) appearing on top of their parent without keyboard focus, requiring a click before typing.

The patch lives on branch `focus-fix-test` and modifies `src/core/window.c` (16-line addition in `meta_window_show()`). It is targeted to coexist with the metacity-derived behaviour from upstream commit `6ea23df` so that GTK xdg_popup completion popups and VLC fullscreen transient controls continue to keep focus on their parent.

Build with `meson setup build && ninja -C build`. The compiled binary at `build/src/marco` is what gets stashed into the system installer at `~/code/system_install_scripts/extras/marco`.

Once the upstream maintainers merge a fix for #784, this fork can be retired.
