# y-loadingscreen
A custom FiveM loading screen. Built with Montserrat, Font Awesome, and a sleek aesthetic.

---

## Screenshots

![Updates](https://i.ibb.co/Y4zrCJkx/Screenshot-2026-03-23-235424.png)
![Team](https://i.ibb.co/tpJR5t51/Screenshot-2026-03-23-235432.png)
![Rules](https://i.ibb.co/DfZ7DM6P/Screenshot-2026-03-23-235439.png)
![Commands](https://i.ibb.co/rGYtNpSs/Screenshot-2026-03-23-235446.png)
![Keybinds](https://i.ibb.co/TMYp275c/Screenshot-2026-03-23-235455.png)

---

## Install

1. Drop the `y-loadingscreen` folder into your server `resources` directory
2. Add to `server.cfg`:
```
ensure y-loadingscreen
setr sv_showBusySpinnerOnLoadingScreen false
```
3. Place your media files in the `assets/` folder (see below)

---

## Assets

Put your files in `assets/` and reference them by filename in the CONFIG:

```
y-loadingscreen/
├── index.html
├── fxmanifest.lua
├── assets/
│   ├── logo.png
│   ├── song1.mp3
│   ├── song2.mp3
│   ├── bg.mp4
│   ├── slide1.jpg
│   ├── slide2.jpg
│   └── slide3.jpg
```

> Any files added to `assets/` must also be listed in the `files {}` block in `fxmanifest.lua`

---

## Configuration

Everything is in the `CONFIG` block of `index.html`. You do not need to touch anything else.

| Option | Description |
|--------|-------------|
| `accentColor` | Hex color for all accents |
| `serverLine1` | Top line of server name |
| `serverLine2` | Bottom line (renders in accent color) |
| `logoSrc` | Path to logo e.g. `assets/logo.png` |
| `backgroundType` | `'slideshow'` or `'video'` |
| `videoSrc` | Path to video file |
| `slides` | Array of image paths for slideshow |
| `slideInterval` | Time per slide in ms (default `7000`) |
| `loadingMessages` | Array of messages — one picked at random on each load |

### Music
```js
music: {
  enabled: true,      // true | false
  volume: 0.5,        // 0.0 to 1.0
  shuffle: false,     // true | false — randomize order on load
  tracks: [
    { src: 'assets/song1.mp3', trackName: 'Song Title', artist: 'Artist' },
    { src: 'assets/song2.mp3', trackName: 'Song Title', artist: 'Artist' },
  ],
},
```

### Socials
```js
socials: [
  { enabled: true, icon: 'fa-discord', label: 'Discord', url: 'https://discord.gg/...' },
  { enabled: true, icon: 'fa-globe',   label: 'Website', url: 'https://...' },
],
// enabled: true | false
// icon: any Font Awesome icon — fa-discord | fa-tiktok | fa-twitch | fa-youtube | fa-instagram | fa-x-twitter | fa-steam | fa-reddit | fa-github | fa-globe | fa-store
// label: 'Text' or '' for icon-only
```

### Tabs
```js
tabs: {
  changelog: { enabled: true, label: 'Updates',  icon: 'updates'  },
  staff:     { enabled: true, label: 'Team',     icon: 'team'     },
  rules:     { enabled: true, label: 'Rules',    icon: 'rules'    },
  commands:  { enabled: true, label: 'Commands', icon: 'commands' },
  keyboard:  { enabled: true, label: 'Keybinds', icon: 'keyboard' },
},
// set enabled: false on any tab to hide it completely
```

### Changelog
```js
changelog: [
  { date: '19 Mar, 2026', title: 'Feature Name', tag: 'New Feature', description: 'Description here.' },
],
```

### Staff
```js
staff: [
  { name: 'Name', role: 'Owner', bio: 'Short bio here.', image: 'assets/avatar.png', link: '' },
],
// image: URL or local path — leave '' for initials placeholder
// link: URL or '' to hide profile button
```

### Rules
```js
rules: [
  { title: 'Rule Title', description: 'Rule description.' },
],
```

### Commands
```js
commands: [
  { command: '/me', description: 'Perform a roleplay action visible to nearby players.' },
],
```

### Keybinds
```js
keybinds: {
  'F1': 'Open Phone',
  'F2': 'Open Inventory',
  // any key name — highlighted keys glow accent color on the keyboard tab
  // hover over a highlighted key to see the action
},
```

---

## Manual Shutdown

The loading screen uses manual shutdown by default. Trigger close from a client script when the player is ready:

```lua
while not LocalPlayer.state.isLoggedIn do
  Wait(500)
end
exports['y-loadingscreen']:closeLoadingScreen()
```

To disable manual shutdown and let FiveM close it automatically, remove `loadscreen_manual_shutdown 'yes'` from `fxmanifest.lua`.

---

## Author
Yeox
