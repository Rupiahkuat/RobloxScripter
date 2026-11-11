
[OPEN SOURCE] RobloxScripter v4.3 - The No-Extension, Native MCP AI Agent for Roblox Studio 🚀

Hey developers,
Tired of clunky AI tools that force you to copy-paste code blocks, track credit meters, or rely on fragile browser extensions that break the moment a web layout updates?
Meet RobloxScripter v4.3 (MCP Edition)—a fully open-source, local AI bridge that hooks professional AI desktop clients directly into Roblox Studio using official, built-in Roblox Model Context Protocol (MCP).
Zero browser extensions. Zero copy-pasting. 100% local server control.
🌐 Official Website & Live Demo: https://mcpgoodscripter.netlify.app/

💎 Why RobloxScripter Over Traditional AI Tools?

Unlike older automation tools that try to scrape web-based AI chats through Chrome extensions, RobloxScripter plugs directly into your professional development environment.
• 🔌 Pure Native Architecture (No Extensions): RobloxScripter doesn’t care about web UI updates. By communicating through native MCP tool calls over studio, your connection is incredibly fast, stable, and unbreakable.
• 📁 Rojo-Style Live Syncing: Your scripts are automatically mirrored as real .lua files on your local machine. You can type in Cursor, VS Code, or Claude Code, and Roblox Studio follows in real-time.
• 🧰 32 Production-Ready Tools: The agent doesn't just hand you code to paste. It reads your whole game tree hierarchy, dynamically modifies scripts, builds UI layouts, alters lighting, shapes terrain, and runs live playtests.
• 📦 Built-in Macro Library (server/macros/): Save your context token limits! RobloxScripter ships with pre-optimized macro templates for standard infrastructure, such as Datastore bootstraps and responsive UI scales, allowing the AI to inject instant boilerplate setups.
• 🛡 Advanced Safety & Control: Every risky action (script edits, deletions, or run_luau calls) prompts a transparent approval review popup inside Roblox Studio. Plus, you can visually review file diffs and undo any changes directly via your local web dashboard (http://127.0.0).

🛠 Supported AI Clients (2026 Industry Standard)

Because the bridge runs through native desktop data pipelines, browser-only chats cannot interface with it. RobloxScripter is purpose-built for the elite desktop clients:
1. Cursor (Recommended for coding workflows)
2. Claude Desktop
3. Claude Code (CLI agent)

⚡ Quick 4-Step Setup Guide

Steps 1–3 are a one-time process.

Step 1: Extract & Install

Extract the release zip folder permanently (e.g., D:\RobloxScripter) and run Install.bat. The setup script automatically fetches a portable Node.js runtime if it’s missing from your PC.

Step 2: Enable the Roblox Studio Plugin

Open Roblox Studio, go to Plugins → RobloxScripter, and select Allow HTTP Requests when prompted.

Step 3: Pair via Local Dashboard

Open your local control panel (http://127.0.0) and click Connect Studio plugin. Your Studio panel will confirm pairing within 60 seconds.

Step 4: Hook your AI Client

Open your AI client's configuration file and plug in the local path to your Mcp.bat:
json
{
  "mcpServers": {
    "roblox-scripter": {
      "command": "D:\\RobloxScripter\\Mcp.bat"
    }
  }
}
Open any game project in Roblox Studio, open your Cursor or Claude chat, and say:
"Take a project snapshot, summarize my game tree, and build a simple checkpoint system."
Watch it execute directly inside your Studio workspace!

⛓ Open Source & Local Security

RobloxScripter is built in plain Lua and JavaScript with no hidden compiled binaries—the code is transparent and auditable. The local server listens strictly on 127.0.0.1 using a cryptographic handshake token, entirely blocking external host/origin request forging.
Stop wrestling with browser extensions and paying per prompt on gated plugins. Elevate your game development workflow with true local AI agency.
🌐 Get Started at Our Website: https://mcpgoodscripter.netlify.app/
