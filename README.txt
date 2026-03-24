INSTALL
-------
1. Drop the y-loadingscreen folder into your server resources directory
2. Add "ensure y-loadingscreen" to your server.cfg
3. Place your files in the resource folder:
     - logo.png       (your server logo)
     - music.mp3      (background music)
     - bg.mp4         (background video, if using video mode)
     - or use image URLs directly in the CONFIG slides array

CONFIGURATION
-------------
Everything is in the CONFIG block at the top of index.html.
You do not need to touch anything else.

  accentColor       Hex color for all accents (default #ca1aff)
  serverLine1       Top line of server name
  serverLine2       Bottom line of server name (accent colored)
  logoSrc           URL or local path to logo image e.g. 'logo.png'

  backgroundType    'slideshow' or 'video'
  videoSrc          Path to bg.mp4 (if using video mode)
  slides            Array of image URLs for slideshow mode
  slideInterval     Time per slide in ms (default 7000)

  loadingText       Text above the loading bar (supports HTML)

  music
    enabled         true/false
    src             Path to music file e.g. 'music.mp3'
    trackName       Song title shown in player
    artist          Artist name shown in player
    volume          Default volume 0.0 to 1.0

  socials           Array of social buttons
    enabled         true/false — hides button and auto-adjusts layout
    icon            Any Font Awesome icon e.g. 'fa-discord', 'fa-tiktok'
    label           Text label — set to '' for icon-only
    url             Link URL

  tabs              Enable/disable individual tabs
    changelog       Updates tab
    staff           Team tab
    rules           Rules tab
    keyboard        Keyboard tab

  changelog         Array of update entries
    date, title, tag, description

  staff             Array of staff members
    name, role, bio, image (URL or ''), link (URL or '')

  rules             Array of rules
    title, description

  keybinds          Object mapping key names to action descriptions
                    e.g. 'F1': 'Open Phone'
                    Bound keys highlight in accent color on the keyboard
                    Hover over a highlighted key to see the action

SHUTDOWN
--------
The loading screen uses manual shutdown. Call the following from
your server-side code when the player is ready to spawn:

  exports['clrp-loadingscreen']:closeLoadingScreen()

Or trigger it client-side:
  TriggerEvent('loadingscreen:close')

If you don't use manual shutdown, remove the line:
  loadscreen_manual_shutdown 'yes'
from fxmanifest.lua and it will close automatically.
