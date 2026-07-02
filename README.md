# Waybar Config

A Waybar configuration for Hyprland with an ashell-inspired light theme with Catppuccin-compatible accent colors.

`style.css` sets the module font stack to:

```css
font-family: "JetBrainsMono Nerd Font", "Noto Sans", monospace;
```

## Dependencies

Install required system packages:

```bash
sudo apt install -y waybar mako-notifier
```

## Fonts

- **JetBrainsMono Nerd Font** — provides the icon glyphs used throughout the
  config (workspace, CPU, memory, network, volume, language, notification,
  battery, etc.). Not packaged in apt, so it was installed manually:

  ```bash
  mkdir -p ~/.local/share/fonts/JetBrainsMono
  curl -fLo ~/.local/share/fonts/JetBrainsMono/JetBrainsMono.zip \
    "https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip"
  unzip ~/.local/share/fonts/JetBrainsMono/JetBrainsMono.zip -d ~/.local/share/fonts/JetBrainsMono
  rm ~/.local/share/fonts/JetBrainsMono/JetBrainsMono.zip
  fc-cache -fv
  ```

  Only the plain `JetBrainsMonoNerdFont-*.ttf` variant was installed (not the
  `NL`, `Mono`, or `Propo` variants) because its embedded family name,
  `JetBrainsMono Nerd Font`, matches what `style.css` requests exactly.

- **Noto Sans** — text fallback for any characters JetBrainsMono Nerd Font
  doesn't cover. Already provided by the system `fonts-noto-core` package, no
  action needed.

After installing fonts, restart waybar (`pkill waybar && waybar &`, or your
Hyprland reload keybind) to pick up the new font.

## Modules

| Module | Description |
|---|---|
| `hyprland/workspaces` | Workspace switcher |
| `hyprland/window` | Active window title |
| `cpu` / `memory` | System resource usage |
| `network` | WiFi/Ethernet status |
| `group/volume` | Volume control via WirePlumber (`wpctl`) |
| `hyprland/language` | Input language switcher |
| `custom/notification` | Notification count via mako |
| `tray` | System tray |
| `battery` | Battery status with charging states |
| `clock` | Date and time |