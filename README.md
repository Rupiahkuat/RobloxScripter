ROBLOXSCRIPTER v4.2  -  Stage 2.0
=================================
New in 4.2:
  1. LOCAL FILE SYNCING (Rojo mini). Folder "src" (next to Start.bat) mirrors every script in Studio as a real file:
       ServerScriptService/Main.server.lua      = Script
       StarterPlayer/StarterPlayerScripts/Ui.client.lua = LocalScript
       ReplicatedStorage/Shared/Utils.lua       = ModuleScript
       Name/init.server.lua (init.client.lua, init.lua) = a script that has child scripts
     - AI writes/edits a script  -> the .lua file on your PC changes.
     - You save a .lua file in VS Code / Cursor -> the script in Studio changes (syntax is checked first; no review
       popup, because the edit comes from you). New files become new scripts.
     - Edits made by hand in Studio are picked up the next time the AI runs a command, or via "Re-sync from Studio".
     - On first connect nothing of yours is overwritten: files that differ from Studio are listed in the dashboard
       and you choose "Use files (push)" or "Use Studio (overwrite)" (old files are backed up in server/.rs_data/backup).
     - Other folder:  node server\server.js --sync-dir D:\MyGame\src     Off:  --no-sync (or the dashboard switch).
     Limits: deleting/renaming a file does not delete the script in Studio (on purpose); a Script with RunContext=Client is
     stored as .server.lua; only scripts under Workspace, ServerScriptService, ReplicatedStorage, ReplicatedFirst,
     ServerStorage, StarterGui, StarterPack, StarterPlayer, Lighting are synced.
  2. ONE-CLICK MACROS in server/tools.json > "commands" (dashboard card "One-click macros"):
       setup_datastore_boilerplate   PlayerDataService + PlayerDataBootstrap in ServerScriptService (skipped if present)
       clean_unused_instances        empty Folders/Models + exact duplicate Parts in Workspace (has Preview / dry-run)
       optimize_ui_scales            UIScale in every ScreenGui + AutoUIScaler LocalScript (has Preview)
     Add your own: copy an entry in tools.json. "actions" are normal tool calls; a string "@file:macros/x.lua" loads the
     text from server/macros/. "unless_exists" skips an action when that path already exists. In run_luau code the
     variable DRY_RUN is injected (true for Preview). Code macros still go through the Studio review popup.
  3. DASHBOARD upgrades: Script history with Diff and Undo (AI / macro / VS Code / manual / undo, survives restarts),
     Error highlighter (header + tab title blink red, optional beep, instant fix idea, code around the failing line,
     "Copy prompt for AI"), sync panel, macro panel, expandable command history.
     Undo of a script the AI created = delete it (Studio asks for approval).
  4. Install.bat / Start.bat: if Node.js 16+ is missing they download the portable LTS build to "runtime\node"
     (no admin rights, SHA-256 verified against nodejs.org) and use it. Nothing is installed system-wide.
  Internal tools sync_script / dump_scripts exist only for the server; /commands rejects them, so the AI cannot use the
  sync path to write scripts without review. Plugin: run Install.bat again (the .lua changed) and restart Studio.
  Tested automatically against a simulated Studio (56 checks) and the dashboard in Chromium. NOT run in real Studio or on
  Windows from here: if the plugin panel or a .bat shows an error, copy it and send it back.

New in 4.1 (on top of v4: same 32 tools, same plugin UI):
  * Local DASHBOARD at http://127.0.0.1:3030/  (server status, Studio sessions, command history with
    durations, tool catalog, EN/ID switch)
  * AUTOMATIC PAIRING: no more copying the token. Click "Connect extension & Studio" in the dashboard;
    for 60 seconds both the browser extension and the Studio plugin fetch the token themselves.
  * Install.bat / Start.bat for Windows (copies the plugin, starts the server, opens the dashboard)
  * Duration timers: per-command total time + plugin run time (dashboard), "· 2.1s" on extension cards,
    "#id selesai - x.xx dtk" in the Studio log.
  * Security: pairing only works inside the 60-second window you open yourself; web pages can never
    claim a token (Origin is checked); the dashboard rejects cross-site requests and has a strict CSP.

REQUIREMENTS
  Node.js 16+ (downloaded automatically by Install.bat/Start.bat if missing). A single .exe comes in Stage 2.1.

FIRST-TIME SETUP (Windows)
  1. Unzip this folder anywhere. Double-click Install.bat.
     - It makes sure Node.js exists (downloads a portable copy if needed), copies the plugin to %LOCALAPPDATA%\Roblox\Plugins and starts the server.
     - The dashboard opens in your browser.
  2. Chrome/Edge: open chrome://extensions, enable Developer mode, "Load unpacked", pick the "extension" folder.
  3. Restart Roblox Studio. Open Plugins > RobloxScripter and click Allow when Studio asks about HTTP.
  4. In the dashboard click "Connect extension & Studio". Within a minute:
       - the Studio panel shows "Pairing otomatis berhasil"
       - the extension panel on an AI site shows "terhubung ke Studio"
     (Manual fallback still works: paste the token from the server console into the extension popup /
      the plugin panel. The popup also has an "Pair otomatis" button.)

DAILY USE
  Double-click Start.bat (server + dashboard), open Studio's RobloxScripter panel, open your AI site.

UPDATING FROM v4
  - Extension: chrome://extensions > Reload on the RobloxScripter card.
  - Plugin: run Install.bat again (or copy the .lua over the old one) and restart Studio.
  - Server: replace the folder; your token file (server/.rs_token) can be kept or deleted (re-pair).

NOTES
  * Everything in the server, dashboard, pairing logic and extension was tested automatically
    (22 server checks + extension auto-claim + dashboard in Chromium). The Studio plugin changes
    (auto-pair + timers) are small, but could not be run inside real Studio from here: if the panel
    shows an error, copy it and send it back.
  * The tool catalog shown in the dashboard comes from server/tools.json (a copy of the list in the extension).
  * UI texts of the extension/plugin are still Indonesian; the dashboard is English by default.
