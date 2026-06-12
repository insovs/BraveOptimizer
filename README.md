<div align="center">

[![Discord Support](https://img.shields.io/badge/Support-Discord-5865F2?logo=discord&logoColor=white)](https://discord.com/invite/fayeECjdtb)
[![Preview](https://img.shields.io/badge/Video-Preview-FF0000?logo=youtube&logoColor=white)](https://youtu.be/9zvIpOmYuK8)
[![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-5391FE?style=flat-square&logo=powershell&logoColor=white)](https://github.com/PowerShell/PowerShell)
[![Platform](https://img.shields.io/badge/Windows-10%2F11-0078D4?style=flat-square&logo=windows&logoColor=white)](https://www.microsoft.com/windows)
[![License](https://img.shields.io/badge/License-MIT-brightgreen?style=flat-square)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0-orange?style=flat-square)](https://github.com/insovs/Brave-Optimizer/releases)

<img src="https://github.com/user-attachments/assets/9a8c646c-3f27-4b42-b9cc-adc1e5b0bed0" alt="Brave Optimizer Banner" width="800"/>

<br/>

## **A PowerShell GUI tool for managing Brave Browser policies & Settings.**

Disable telemetry, Bloat, remove unwanted features, and fine-tune privacy and performance, all from a single interface. No manual registry editing, no config files to hunt down. Just run, configure, and apply.








## ❓ FAQ

<details>
<summary><strong>Is this safe to use?</strong></summary>

Yes. The tool only removes files that Discord does not need to function (old versions, unused language packs, cache, telemetry modules). Nothing related to your account, messages, or servers is touched. You can enable the **backup option** in Advanced settings before running anything, which saves a full copy of your Discord folder to the Desktop.

</details>

<details>
<summary><strong>My antivirus flagged the script — is it a virus?</strong></summary>

No. PowerShell scripts that interact with the filesystem are commonly flagged as false positives by heuristic-based antivirus engines, especially when they modify program files or registry keys. This script contains no malicious code. You can verify this yourself:

- 📄 **The script is fully open-source** — read every line on this page before running it
- 🔍 **VirusTotal scan:** [View latest scan results →](https://www.virustotal.com/gui/url/YOUR_SCAN_LINK_HERE)

If your antivirus blocks execution, you may need to add a temporary exception or use:
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

</details>

<details>
<summary><strong>Will this survive a Discord update?</strong></summary>

Partially. Discord updates reinstall some of the removed components (language packs, modules) since they ship a fresh install on each update. After a major Discord update, it is recommended to re-run the tool. The **Clean Cache** section is always safe to re-run at any time.

</details>

<details>
<summary><strong>Is it compatible with BetterDiscord / Vencord / other mods?</strong></summary>

Generally yes. The tool does not touch injection files or mod-related assets. However, if you use a client mod, it is recommended to enable the **backup option** before debloating, and to avoid removing the auto-updater (as some mods rely on the update flow to re-inject themselves).

</details>

<details>
<summary><strong>I removed Game Presence / RPC and now FiveM / my game launcher can't link my account.</strong></summary>

The Game Presence module (`discord_game_sdk`) is required for some games (FiveM, certain launchers) to link your Discord account. To restore it: re-install Discord, or restore from the backup saved on your Desktop if you had the backup option enabled.

</details>

<details>
<summary><strong>My Discord settings reset after cleaning the cache. Is that normal?</strong></summary>

Some UI preferences (font size, theme, notification settings) are stored in cache and will reset after a full cache clean. Your **account session** and **server data** are unaffected. If you opted into removing **Local Storage**, you will be signed out and need to log back in — this is clearly warned in the tool.

</details>

<details>
<summary><strong>Does this work on Discord PTB and Canary?</strong></summary>

Yes. The tool auto-detects which Discord variants are installed (Stable, PTB, Canary) and displays them with color-coded status indicators. You can run it on any detected variant.

</details>

<details>
<summary><strong>Can I restore my original Discord after debloating?</strong></summary>

Yes, if you enabled the **backup option** before running. A full copy of your Discord installation is saved to your Desktop. To restore: close Discord, delete the current installation folder, rename the backup to the original folder name, and relaunch.

Alternatively, a clean reinstall from [discord.com](https://discord.com) will restore everything.

</details>











<br/>

</div>

---

## 📥 Installation

```powershell
iwr "https://raw.githubusercontent.com/insovs/Brave-Optimizer/main/BraveOptimizer.ps1" -OutFile "BraveOptimizer.ps1"; .\BraveOptimizer.ps1
```

> [!NOTE]
> If PowerShell scripts are blocked on your system, use **[EnablePowerShellScript](https://github.com/insovs/EnablePowerShellScript)** to enable and revert execution policy in one click.

---

## ⚙️ Features
<details>
<summary><strong>View all</strong></summary>
<br/>

| Category | Policy | Description |
|---|---|---|
| **Extensions** | uBlock Origin Lite (MV3) | Force-installs uBO Lite from the Chrome Web Store (set to "Optimal" mode) |
| **Extensions** | uBlock Origin (MV2) | Force-installs full uBO — activate via `brave://settings/extensions/v2` |
| **Telemetry** | Disable Metrics Reporting | Blocks usage statistics and crash reports sent to Brave / Google |
| **Telemetry** | Disable Safe Browsing Reporting | Stops visited URLs being sent to Google for threat analysis |
| **Telemetry** | Disable URL Data Collection | Disables anonymized URL collection tied to your profile |
| **Telemetry** | Disable Feedback Surveys | Removes satisfaction survey popups sent by Brave |
| **Telemetry** | Disable User Feedback | Disables the built-in user feedback system entirely |
| **Privacy** | Disable Safe Browsing | Disables Google anti-phishing/malware filter (uBO covers the essentials) |
| **Privacy** | Disable Autofill (Addresses) | Stops saving and auto-filling postal addresses in forms |
| **Privacy** | Disable Autofill (Credit Cards) | Prevents Brave from saving or suggesting credit card numbers |
| **Privacy** | Disable Web Payment API | Blocks websites from detecting your registered payment methods |
| **Privacy** | Disable Password Manager | Disables the native password manager — use Bitwarden or similar |
| **Privacy** | Disable Browser Sign-in | Prevents signing into Google or Brave accounts, blocks cloud sync |
| **Privacy** | Disable WebRTC IP Leak | Forces WebRTC to use proxied interfaces only — prevents VPN IP leaks |
| **Privacy** | Disable QUIC Protocol | Disables Google's UDP/HTTP3 protocol which can bypass proxies |
| **Privacy** | Block Third-Party Cookies | Blocks cookies set by ad trackers, analytics, and social widgets |
| **Privacy** | Enable Do Not Track | Sends `DNT: 1` header with every request |
| **Privacy** | Force SafeSearch | Enforces SafeSearch across all Google searches |
| **Privacy** | Disable Incognito Mode | Blocks access to private / incognito windows |
| **Privacy** | Disable IPFS | Removes IPFS support and the `ipfs://` protocol handler |
| **Brave Features** | Disable Brave Rewards (BAT) | Removes the BAT token system and toolbar button |
| **Brave Features** | Disable Brave Wallet | Disables the built-in crypto wallet (ETH, SOL, etc.) |
| **Brave Features** | Disable Brave VPN | Removes the paid VPN integration from the UI |
| **Brave Features** | Disable Leo AI Assistant | Disables Leo, Brave's built-in AI assistant — removes sidebar button |
| **Brave Features** | Disable Brave News | Removes the Brave News feed from the new tab page |
| **Brave Features** | Disable Brave Talk | Disables the built-in Jitsi-based video conferencing service |
| **Brave Features** | Disable Tor | Removes Tor / onion routing from private windows |
| **Brave Features** | Disable Sync | Blocks cross-device sync of bookmarks, history, and passwords |
| **Brave Features** | Disable Brave Shields | Disables Brave's built-in ad/tracker blocking for all URLs |
| **New Tab & UI** | Disable NTP Cards and Widgets | Hides new tab widgets: weather, sponsored sites, clock, wallpaper |
| **New Tab & UI** | Restrict Top Sites Shortcuts | Limits NTP shortcuts to allowed TLDs — blocks sponsored suggestions |
| **New Tab & UI** | Disable Auto Translate | Stops Brave from offering to translate foreign pages via Google |
| **New Tab & UI** | Disable Spellcheck | Turns off spellcheck across all input fields |
| **New Tab & UI** | Disable Online Spellcheck Service | Stops text being sent to Google / Grammarly for spell checking |
| **New Tab & UI** | Disable Search Suggestions | Prevents keystrokes being sent to your search engine before submitting |
| **New Tab & UI** | Disable Brave Promotions | Removes VPN offers, Wallet banners, and subscription prompts |
| **New Tab & UI** | Disable Default Browser Prompt | Stops Brave from asking to become the default browser |
| **Performance** | Disable Background Mode | Brave stops running after closing — reduces idle CPU and RAM |
| **Performance** | Disable Media Recommendations | Removes video/podcast suggestions from sidebar and new tab |
| **Performance** | Disable Shopping List | Removes price-tracking on e-commerce pages |
| **Performance** | Always Open PDF Externally | Forces PDFs to download instead of opening in-browser |
| **Performance** | Disable Printing | Disables `Ctrl+P` / web page printing entirely |
| **Performance** | Disable Developer Tools | Blocks F12 / DevTools access entirely |
| **DNS** | DNS Over HTTPS Mode | Configure DoH as `automatic`, `off`, or `custom` |

</details>

## 🎛️ Presets

<details>
<summary><strong>Privacy</strong></summary>
<br/>

| Group | Behavior |
|---|---|
| Telemetry | Blocks all reporting: metrics, Safe Browsing, URL collection, surveys, user feedback |
| Privacy | Disables autofill, payment API, password manager, browser sign-in, WebRTC leaks, QUIC — blocks third-party cookies, forces DNT |
| Brave Features | Kills Rewards, Wallet, VPN, AI Chat, News, Talk, Tor, and Sync |
| New Tab & UI | Hides NTP widgets, restricts top site shortcuts, disables translate, spellcheck, search suggestions, and promotions |
| Performance | Disables background mode, media recommendations, and shopping list |
| Extension | Force-installs uBlock Origin Lite (MV3) |
| DNS | Plain DNS (`off`) — avoids logging by DoH providers |

</details>

<details>
<summary><strong>Performance</strong></summary>
<br/>

| Group | Behavior |
|---|---|
| Telemetry | Blocks all reporting: metrics, Safe Browsing, URL collection, surveys, user feedback |
| Privacy | Disables autofill, payment API, password manager, browser sign-in, WebRTC leaks — blocks third-party cookies, forces DNT, disables incognito |
| Brave Features | Kills Rewards, Wallet, VPN, AI Chat, News, Talk, Tor, Sync, and Shields |
| New Tab & UI | Hides NTP widgets, restricts top site shortcuts, disables translate, spellcheck, search suggestions, promotions, and default browser prompt |
| Performance | Disables background mode, media recommendations, shopping list, printing, and DevTools |
| DNS | Custom DoH — configure your own resolver in `brave://settings/security` |

</details>

<details>
<summary><strong>Performance & Privacy</strong></summary>
<br/>

| Group | Behavior |
|---|---|
| Telemetry | Blocks all reporting: metrics, Safe Browsing, URL collection, surveys, user feedback |
| Privacy | Disables autofill, payment API, password manager, browser sign-in, WebRTC leaks, QUIC — blocks third-party cookies, forces DNT |
| Brave Features | Kills Rewards, Wallet, VPN, AI Chat, News, Talk, Tor, Sync, and Shields |
| New Tab & UI | Hides NTP widgets, restricts top site shortcuts, disables translate, spellcheck, search suggestions, promotions, and default browser prompt |
| Performance | Disables background mode, media recommendations, shopping list, and printing — PDFs always open externally |
| DNS | Plain DNS (`off`) — avoids logging by DoH providers |

</details>

---

## 💾 Export / Import

Configurations are saved as plain JSON — easy to version, share, or commit alongside your dotfiles.

```json
{
  "Features": [
    "MetricsReportingEnabled",
    "SafeBrowsingExtendedReportingEnabled",
    "ext:cjpalhdlnbpafiamejdnhcphjbkeiagm"
  ],
  "DnsMode": "automatic"
}
```

---

## Verify

After applying policies, open Brave and navigate to:

```
brave://policy
```

All active policies will be listed there. If a policy is missing, fully restart Brave.

> [!TIP]
> Applied policies override Brave's settings UI — affected options will display **"Managed by your organization."**  
> Run **Reset All** at any time to wipe all policies and return to defaults.

---

## License

MIT — free to use, modify, and distribute.

---

<div align="center">

Made by [insovs](https://guns.lol/inso.vs)

</div>
