# RiotVault

> **Effortlessly switch between multiple Riot Games accounts — with a secure, encrypted local vault.**

RiotVault is a lightweight Windows desktop application that lets you manage and instantly switch between multiple Riot Games accounts. It stores your credentials locally using Windows DPAPI encryption and injects them directly into the Riot Client — no cloud, no telemetry, no third-party servers.

---

## ✨ Features

- 🔐 **Secure Local Vault** — Credentials are encrypted at rest using Windows DPAPI (device-bound, user-scoped). Nothing leaves your machine.
- ⚡ **One-Click Account Switching** — Switch accounts in seconds without manually logging out and back in.
- 🖼 **Overlay UI** — A clean, non-intrusive overlay that appears on demand and stays out of your way.
- 🌐 **Multi-Language** — English and French supported out of the box.
- 📦 **Portable or Installed** — Run from anywhere as a single self-contained `.exe`, or install via the Setup wizard.
- 🔄 **Backward Compatible** — Seamlessly migrates vault data from legacy RiotSwitch installations.
- 🩺 **CLI Doctor Tool** — Built-in CLI (`RiotVault.Cli.exe doctor`) to verify your vault and configuration.

---

## 📥 Download

| Package | Description |
|---------|-------------|
| [**RiotVault-Setup-x64-1.0.0.exe**](https://github.com/KaleidSkylark/RiotVault/releases/latest) | Recommended. Installer with optional desktop shortcut and auto-start. Requires [.NET 8 Desktop Runtime (x64)](https://dotnet.microsoft.com/download/dotnet/8.0). |
| [**RiotVault-Portable.exe**](https://github.com/KaleidSkylark/RiotVault/releases/latest) | Self-contained, no installation needed. Run from any folder. No .NET runtime required. |

> Download the latest build from the [**Releases**](https://github.com/KaleidSkylark/RiotVault/releases/latest) page.

---

## 🚀 Getting Started

### Portable
1. Download `RiotVault-Portable.exe` from [Releases](https://github.com/KaleidSkylark/RiotVault/releases/latest).
2. Place it anywhere you like (e.g. `C:\Tools\RiotVault\`).
3. Double-click to launch. The vault and settings are stored in `%LOCALAPPDATA%\RiotVault`.

### Setup Installer
1. Download `RiotVault-Setup-x64-1.0.0.exe` from [Releases](https://github.com/KaleidSkylark/RiotVault/releases/latest).
2. Run the installer. It will check for the .NET 8 Desktop Runtime and prompt you to download it if missing.
3. Optionally enable **"Start with Windows"** during setup for automatic background launch.

### First Run
1. Launch RiotVault.
2. The overlay appears — click **Add Account** and log in through the Riot Client normally.
3. RiotVault captures and encrypts your session. Future switches happen instantly.

---

## 🗂 Vault Data & Compatibility

- Vault data is stored in: `%LOCALAPPDATA%\RiotVault`
- **Upgrading from RiotSwitch?** RiotVault automatically detects and uses your existing `%LOCALAPPDATA%\RiotSwitch` vault if no new vault exists yet. Your accounts migrate seamlessly — no manual steps needed.

---

## 🔒 Security & Privacy

| Property | Detail |
|----------|--------|
| **Encryption** | Windows DPAPI — credentials are bound to your Windows user account and device |
| **Network** | Communicates only with the local Riot Client loopback interface (`127.0.0.1`) |
| **Telemetry** | None. Zero data collection. |
| **Storage** | 100% local — no accounts, no cloud sync, no external servers |

RiotVault never transmits your credentials over the network. It reads and writes the same local session files the Riot Client uses natively.

---

## 🛠 Building from Source

### Requirements
- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) (Windows x64)
- Windows 10/11 x64
- [Inno Setup 6](https://jrsoftware.org/isinfo.php) *(optional — only needed to build the installer)*

### Build & Test
```powershell
# Clone
git clone https://github.com/KaleidSkylark/RiotVault.git
cd RiotVault

# Build
dotnet build RiotVault.sln

# Run tests
dotnet test RiotVault.sln
```

### Publish
```powershell
# Standard publish (requires .NET 8 Desktop Runtime on target machine)
.\tools\publish.ps1

# Self-contained portable single-file exe (~64 MB, no runtime needed)
.\tools\publish-singlefile.ps1
```

Output: `builds/app-latest/` and `builds/portable-latest/`

### Build Installer *(optional)*
```powershell
& 'C:\Program Files (x86)\Inno Setup 6\ISCC.exe' installer\RiotVault.iss /DMyAppVersion=1.0.0
```
Output: `builds/installer/RiotVault-Setup-x64-1.0.0.exe`

---

## 🧰 CLI Tool

RiotVault ships with a companion CLI for diagnostics:

```
RiotVault.Cli.exe doctor        # Check vault health and configuration
RiotVault.Cli.exe list          # List all stored accounts
```

---

## ⚠️ Disclaimer

RiotVault is an independent, community-built tool. It is **not affiliated with, endorsed by, or supported by Riot Games, Inc.** in any way.

- "Riot Games", "League of Legends", "VALORANT", and all related marks are trademarks of Riot Games, Inc.
- Use of this tool is at your own risk. The authors are not responsible for any account actions taken by Riot Games.
- RiotVault only uses the officially documented Riot Client local API (loopback interface).

---

## 🙏 Attribution

RiotVault is a derivative of [quentingimenez/RiotSwitch](https://github.com/quentingimenez/RiotSwitch). Original work © quentingimenez. The original repository does not carry a license; redistribution of this derivative requires permission from the original author.

---

## 📄 License

No open-source license is applied at this time. All rights reserved.
Redistribution, modification, or commercial use is not permitted without explicit written permission.
