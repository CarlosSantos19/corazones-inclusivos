# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static web-based interactive game/presentation about Angie Duarte, built as a single HTML file with inline CSS and JavaScript. The project uses a retro 8-bit Super Mario-inspired aesthetic to present personal and professional information through an interactive platformer-style interface.

## Architecture

**Single-File Structure**: The entire application is contained in `angie.html` (with variants `angie2.html` and `angie3.html`). All HTML, CSS, and JavaScript are included inline - there are no external dependencies, build tools, or frameworks.

**Key Components**:
- **Game Engine**: Pure JavaScript with no frameworks. Uses DOM manipulation and CSS animations for game mechanics
- **Audio System**: Web Audio API for 8-bit style sound effects and music (no external audio files required)
- **Modal System**: Multiple overlay modals for displaying photos and information
- **Control System**: Robot character controlled via on-screen buttons or keyboard (WASD/arrows + spacebar)

**Game Flow**:
1. Start screen → Scroll intro (pergamino) → Game area
2. Player controls robot to collect 4 items (💼, 👨‍👩‍👧‍👦, 🎮, 🎯)
3. Each collected item shows photos from the `/FOTO*.png` files
4. Victory screen appears when all items are collected and finish flag is reached

**Data Structure**: The `gameData` object (starting at line 1259) defines:
- `skill`, `family`, `hobby`, `goal` - each with title, photos array, and descriptive text
- Photos are referenced by filename and must exist in the root directory

## Development Commands

**Running the Application**:
```bash
# Open angie.html directly in a browser (double-click or drag-and-drop)
# OR use VSCode Live Server (configured on port 5502)
```

**No Build Process**: This is a static HTML file. Simply open it in any modern web browser.

## File Organization

```
/ANGIE/
├── angie.html       # Main game (latest version)
├── angie2.html      # Variant version
├── angie3.html      # Variant version
├── FOTO1.png        # Skill/professional photo
├── FOTO2.png        # Family photo 1
├── FOTO2(2).png     # Family photo 2
├── FOTO3.png        # Hobby photo 1
├── FOTO3(2).png     # Hobby photo 2
└── FOTO4.png        # Goals/expectations photo
```

## Modifying Content

**Changing Text/Information**: Edit the `gameData` object in the `<script>` section (around line 1259-1280).

**Adding/Removing Photos**:
- Update the `photos` array in the relevant `gameData` entry
- Ensure image files exist in the root directory
- The photo carousel automatically adapts to the array length

**Styling Changes**: All CSS is in the `<style>` section (lines 7-959). Key classes:
- `.carlos-character` - main static character
- `.auto-character` - controllable robot
- `.collectible` - interactive items to collect
- `.platform` - visual platforms (non-interactive)
- `.gif-modal` - photo display modal

**Audio Customization**:
- `mainMelody` array (line 1150) - defines the 8-bit background music notes
- Sound functions (`createBeep`, `playCollectSound`, etc.) generate procedural audio

## Technical Notes

- **Browser Compatibility**: Requires Web Audio API support (all modern browsers)
- **No Server Required**: Can run from `file://` protocol
- **Responsive Design**: Basic mobile support via media queries (@media max-width: 768px)
- **Keyboard Controls**: WASD/Arrow keys for movement, Spacebar to collect, Escape to close modals
