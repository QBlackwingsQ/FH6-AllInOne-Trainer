# FH6 All-in-One Trainer

An all-in-one trainer for **Forza Horizon 6** — runtime hooks for player profile values + car/physics cheats + live SQL access to the game's in-memory database. Single-file `.exe`, no extra runtime needed.

> Use at your own risk. This trainer modifies game memory. Microsoft / Playground Games can ban your account. **Solo / Free Roam only — never use online (Rivals, Eventlab, Multiplayer, leaderboards).**

## Download

Latest release: **[GitHub Releases](../../releases)** — download the `.zip`, extract, and run `FH6AllInOneTrainer.exe` as Administrator. Self-contained — no .NET install needed.

## Working Features

### Quick Actions
- **Quick Start** — 999M Credits + Free Cars + Autoshow Unlock + All Cars, one click
- **Max All** — Credits 999M, Wheelspins 999, Super Wheelspins 999, Skill Points 999K

### Profile Values (NOP-sled memory hooks)
- **Credits (CR)** — prevents credit deduction with presets (10K to 999M)
- **Wheelspins** — prevents wheelspin consumption (10 to 999)
- **Super Wheelspins** — prevents super wheelspin consumption
- **Skill Points** — prevents skill point spending (100 to 999K)
- **Sell Payout x** — multiply car sell price by any factor

### Racing & World
- **Freeze AI** — stops all AI Drivatar cars during races
- **Teleport to Waypoint** — instantly teleport to any map waypoint
- **Gravity Multiplier** — adjust gravity (0.5x moon, 2x heavy, etc.)
- **No Water Drag** — remove water resistance
- **Time of Day** — set any hour (6=dawn, 12=noon, 18=dusk, 0=midnight)
- **Acceleration Override** — boost car acceleration with custom multiplier
- **Free Clothing** — set all clothing prices to 0

### Scoring & Rewards
- **Drift Score Multiplier** — multiply drift scoring (5x, 10x, 50x)
- **Skill Score Multiplier** — multiply skill chain score (10x, 100x)
- **Prize Scale** — multiply wheelspin reward value
- **Speed Trap Multiplier** — multiply speed trap score
- **Skill Score Multiplier** — multiply earned skill score

### Timers
- **Race Time Scale** — slow down or freeze race timer (0 = freeze)
- **Mission Time Scale** — slow down or freeze mission timer
- **Remove Build Cap** — remove engine swap / build power limit

### SQL Database (in-memory SQLite)
- **Unlock Everything** — all SQL cheats in one click
- **Free Cars (LOCK)** — BaseCost stays at 0 (re-applied every 10s)
- **Autoshow All Visible (LOCK)** — every car in showroom
- **Install Flags (LOCK)** — IsInstalled/IsPurchased/IsDrivable stay at 1
- **Add All Cars** — grant every car free
- **Free Upgrades** — price=0 on all 47 upgrade tables
- **Free Wheels** — price=1 on all wheels
- **Full Autoshow** — complete autoshow with CarBuckets

### Physics & Performance (SQL)
- **Drift Score 10x** — sets DriftScoreScalar=10.0 on all tracks
- **Max Traction (Grip Hack)** — massive grip increase on all cars + wet tire compounds
- **Torque Scale 2x** — doubles engine torque output
- **Reduce Drag 0.5x** — halves aero drag for higher top speed

## Anti-Cheat Bypass

- **CRC bypass** — vtable function pointer swap with 5s heartbeat + random jitter
- **Value Encryption bypass** — RET at encryption function prologue, keeps profile values in plaintext
- **5 integrity check patches** — TextSection hash, PageHash, MemCmp, CodeSection verify, Checksum verify
- **Thread-safe patching** — all FH6 threads suspended during CRC heartbeat dance
- **ExpectedOriginal sanity check** — refuses to inject if target bytes don't match
- **Auto-detach** when game exits

## Still Broken
These cheats exist in the UI but don't work (broken across ALL known FH6 trainers):
- NoClip — hooks wrong function (string/hash compare, not collision)
- No Skill Break — signature found but unreliable
- XP Override — address not found in FH6
- God Mode — not yet implemented

## Build from Source

Requires **.NET 10 SDK** on Windows:

```bash
dotnet publish -c Release -r win-x64 --self-contained
```

Output: `bin/Release/net10.0-windows/win-x64/publish/FH6AllInOneTrainer.exe`

## Credits

| Who | Contribution |
|-----|-------------|
| **[paris' club](https://discord.gg/WSd3bRNJuJ)** | Core cheats: runtime hooks, SQL features, CRC bypass |
| **[ForzaMods](https://github.com/ForzaMods/Forza-Mods-AIO)** | AOB signatures for hook-based cheats |
| **[Omkmakwana](https://github.com/Omkmakwana/FH6Trainer)** | NOP-sled approach for Credits/Wheelspins/SkillPoints |
| **[matkhl](https://www.unknowncheats.me/forum/other-games/752793)** | Free Upgrades SQL (47 tables), database dumper |
| **[Chaarkor](https://github.com/Chaarkoor)** | Original Avalonia UI shell, MVVM architecture |
| **[changcheng967](https://github.com/changcheng967)** | All-in-one improvements, physics SQL cheats, value encryption bypass |

## License

GPL-3.0 — source must remain open. See [LICENSE](LICENSE).
