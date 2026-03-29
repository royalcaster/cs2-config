# CS2 Performance Guide

Everything beyond `autoexec.cfg` that can squeeze more frames out of your machine.

---

## Steam Launch Options

Right-click CS2 in Steam > Properties > Launch Options:

```
-fullscreen -novid -nojoy -high +exec autoexec.cfg
```

| Option | What it does |
|---|---|
| `-fullscreen` | Exclusive fullscreen -- lowest input lag |
| `-novid` | Skips the Valve intro video |
| `-nojoy` | Disables joystick polling, frees minor CPU |
| `-high` | Sets CS2 to high CPU/RAM priority in Windows |
| `+exec autoexec.cfg` | Ensures your autoexec runs every launch |

**Avoid these outdated CS:GO options** (they do nothing or cause issues in CS2):
`-heapsize`, `-threads`, `-nod3d9ex`, `+mat_queue_mode`, `-tickrate 128`, `-insecure`

---

## In-Game Video Settings

These have the biggest impact on raw FPS. Ordered by performance impact (highest first):

| Setting | Recommended | Notes |
|---|---|---|
| Display Mode | **Fullscreen** | Never use windowed/borderless for competitive |
| Resolution | **1280x960 (4:3 stretched)** | ~30-50% more FPS vs 1080p. Use native 1080p if you prefer clarity. |
| V-Sync | **Disabled** | Adds input lag, always off |
| Multisampling AA | **None** or **2x MSAA** | Big FPS cost, minimal visual gain |
| Global Shadow Quality | **Low** | Huge FPS saver |
| Texture Detail | **Low-Medium** | Medium if you have enough VRAM (4GB+) |
| Shader Detail | **Low** | Reduces GPU workload noticeably |
| Particle Detail | **Low** | Directly affects smoke grenade performance |
| Ambient Occlusion | **Disabled** | Adds visual clutter and costs frames |
| Dynamic Shadows | **Off** if available | Saves CPU cycles |
| Motion Blur | **Disabled** | Costs FPS and makes everything harder to see |

### Resolution Cheat Sheet

| Resolution | Aspect | FPS Impact |
|---|---|---|
| 1920x1080 | 16:9 | Baseline |
| 1680x1050 | 16:10 | ~10-15% boost |
| 1280x960 | 4:3 Stretched | ~30-50% boost |
| 1024x768 | 4:3 Stretched | ~50-70% boost (very blurry) |

---

## NVIDIA Control Panel Settings

Open NVIDIA Control Panel > Manage 3D settings > Program Settings > add `cs2.exe`:

| Setting | Value |
|---|---|
| Power Management Mode | **Prefer Maximum Performance** |
| Low Latency Mode | **Ultra** (or use NVIDIA Reflex in-game) |
| Ambient Occlusion | **Off** |
| Antialiasing - FXAA | **Off** |
| Anisotropic Filtering | **Application-controlled** |
| Image Scaling | **Off** |
| Threaded Optimization | **On** |
| Texture Filtering Quality | **High Performance** |
| Vertical Sync | **Off** |
| Max Frame Rate | **Off** |

### NVIDIA Reflex

If your GPU supports it, enable **NVIDIA Reflex** in CS2's in-game settings (set to **Enabled + Boost**). This reduces system latency significantly and is more effective than the control panel Low Latency Mode.

---

## AMD GPU Settings (Radeon Software)

| Setting | Value |
|---|---|
| Radeon Anti-Lag | **Enabled** |
| Radeon Chill | **Disabled** |
| Wait for Vertical Refresh | **Always Off** |
| Anisotropic Filtering | **Application-controlled** |
| Anti-Aliasing | **Use application settings** |
| Texture Filtering Quality | **Performance** |
| Surface Format Optimization | **Enabled** |

---

## Windows Optimization

### Power Plan
Settings > System > Power & battery > Power mode > **Best performance**

Or via Control Panel: Power Options > **High Performance** (or **Ultimate Performance** if available -- enable it with `powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61` in an admin terminal).

### Game Mode
Settings > Gaming > Game Mode > **Off**

Game Mode can cause micro-stutters in CS2. Turn it off.

### Hardware-Accelerated GPU Scheduling
Settings > System > Display > Graphics > **Turn on** Hardware-accelerated GPU scheduling

Reduces latency on modern GPUs (requires restart).

### Background Apps
- Close Discord overlay, Steam overlay if not needed
- Close browser tabs (Chrome/Edge eat RAM)
- Disable startup apps you don't need (Task Manager > Startup)
- Close RGB software, hardware monitoring tools while playing

### Fullscreen Optimization
Right-click `cs2.exe` > Properties > Compatibility > check **Disable fullscreen optimizations**

Path: `Steam\steamapps\common\Counter-Strike Global Offensive\game\bin\win64\cs2.exe`

---

## Monitoring Your FPS

Useful commands to check if changes are working:

```
cl_showfps 1          // Simple FPS counter (top-left)
cq_netgraph 1         // Detailed overlay: FPS, ping, packet loss, tick
```

Turn them off with `cl_showfps 0` / `cq_netgraph 0`.

---

## Quick Checklist

- [ ] Launch options set in Steam
- [ ] Autoexec runs on startup (`+exec autoexec.cfg`)
- [ ] In-game video settings lowered
- [ ] V-Sync off everywhere (in-game + GPU driver)
- [ ] GPU driver up to date
- [ ] NVIDIA/AMD control panel configured for CS2
- [ ] Windows power plan set to High Performance
- [ ] Game Mode disabled
- [ ] Background apps closed
- [ ] Fullscreen optimizations disabled on cs2.exe
