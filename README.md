# Cymatics - Orbital Sound Visualizer

A Progressive Web App (PWA) that visualizes sound through atomic orbital geometry patterns. Experience real-time audio visualization with mesmerizing cymatics-inspired graphics that respond to microphone input or audio files.

![Cymatics Visualizer](icons/icon-192.png)

## Features

- **Real-time Audio Visualization** — See your music or voice come alive with dynamic orbital patterns
- **Dual Input Sources** — Use your microphone or upload audio files
- **Atomic Orbital Geometry** — Physics-based visualization inspired by Chladni patterns and atomic orbitals
- **Interactive Controls** — Adjust complexity, symmetry, sensitivity, and rotation in real-time
- **Audio Analysis Display** — View frequency and energy levels as you listen
- **Playback Controls** — Full-featured audio player with progress bar and volume control
- **PWA Support** — Install as a standalone app on mobile and desktop
- **Offline Capable** — Works without internet after initial load

## Live Demo

Open `index.html` in a modern web browser or deploy to any static hosting service.

## Installation

### As a PWA (Recommended)

1. Open the app in a supported browser (Chrome, Edge, Safari)
2. Tap the "Add to Home Screen" or "Install" prompt
3. Launch Cymatics as a standalone app

### Manual Setup

```bash
# Clone or download the repository
git clone <repository-url>

# Navigate to the project directory
cd cymatics

# Serve with any static file server
# Python 3
python -m http.server 8000

# Node.js (npx)
npx serve .

# PHP
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

## Usage

1. **Launch the app** — You'll see the start screen with two options
2. **Choose input method:**
   - **Microphone** — Visualize live audio from your device's microphone
   - **Audio File** — Upload and visualize any audio file (MP3, WAV, etc.)
3. **Adjust visualization** — Tap the settings icon to customize:
   - **Complexity** (3-12) — Number of harmonic patterns
   - **Symmetry** (4-16) — Rotational symmetry of the pattern
   - **Sensitivity** (0.2-3.0) — Audio reactivity level
   - **Rotation** (0-2) — Pattern rotation speed
4. **Enjoy the show** — Watch as the orbital geometry dances to your audio

## File Structure

```
cymatics/
├── index.html          # Main application file
├── manifest.json       # PWA manifest
├── sw.js              # Service worker for offline support
├── icons/             # App icons (multiple sizes)
│   ├── icon-72.png
│   ├── icon-96.png
│   ├── icon-128.png
│   ├── icon-144.png
│   ├── icon-152.png
│   ├── icon-192.png
│   ├── icon-384.png
│   ├── icon-512.png
│   └── icon.svg       # Source SVG icon
├── generate-icons.html # Icon generation utility
└── placeholder.html    # Placeholder page
```

## Technical Details

### Built With

- **Vanilla JavaScript** — No frameworks, pure performance
- **Web Audio API** — Real-time audio analysis and processing
- **Canvas 2D API** — Hardware-accelerated graphics rendering
- **Service Workers** — Offline caching and PWA functionality
- **Web App Manifest** — Native app-like experience

### Audio Processing

- **FFT Size:** 1024 bins for frequency analysis
- **Frequency Bands:** Bass (0-250Hz), Mid (250-2000Hz), High (2000Hz+)
- **Smoothing:** 0.8 time constant for fluid visualization
- **Sample Rate:** Native device sample rate

### Visualization Engine

The app uses a multi-layered orbital pattern system:

1. **Layer 1 (Bass)** — Inner orbit, blue tones, responds to low frequencies
2. **Layer 2 (Mid)** — Middle orbit, purple tones, responds to mid frequencies
3. **Layer 3 (High)** — Outer orbit, pink tones, responds to high frequencies
4. **Layer 4 (Energy)** — Ambient layer, responds to overall volume

Each layer generates vertices along orbital paths with harmonic modulation, creating the characteristic atomic orbital appearance. Euclidean geometry connects vertices between layers for additional visual complexity.

## Browser Support

| Browser | Support |
|---------|---------|
| Chrome 80+ | ✅ Full |
| Firefox 75+ | ✅ Full |
| Safari 13+ | ✅ Full |
| Edge 80+ | ✅ Full |
| Opera 67+ | ✅ Full |

**Requirements:**
- Web Audio API support
- Canvas 2D support
- ES6+ JavaScript

## Permissions

The app requests the following permissions:

- **Microphone** — For live audio visualization (only when selected)
- **File Access** — For uploading audio files (user-initiated only)

No audio data is stored or transmitted — all processing happens locally in your browser.

## Customization

### Adjusting Default Settings

Edit the `CONFIG` object in `index.html`:

```javascript
const CONFIG = {
    fftSize: 1024,        // Frequency analysis resolution
    smoothing: 0.8,       // Audio smoothing (0-1)
    complexity: 5,        // Default pattern complexity (3-12)
    symmetry: 8,          // Default symmetry (4-16)
    sensitivity: 1.0,     // Default sensitivity (0.2-3.0)
    rotationSpeed: 0.5    // Default rotation speed (0-2)
};
```

### Changing Colors

Modify the `layers` array in the `drawOrbitalPattern` function:

```javascript
const layers = [
    { radiusMult: 0.3, audioMult: bass, color: [80, 120, 255], width: 2 },   // Blue
    { radiusMult: 0.5, audioMult: mid, color: [150, 100, 255], width: 1.5 }, // Purple
    { radiusMult: 0.7, audioMult: high, color: [200, 150, 255], width: 1 },  // Pink
    { radiusMult: 0.9, audioMult: energy, color: [255, 200, 255], width: 0.5 } // White-pink
];
```

## Performance Tips

- Use a device with hardware acceleration for best results
- Close other browser tabs to free up resources
- Lower `complexity` and `symmetry` values on slower devices
- The app automatically adjusts for high-DPI displays

## Troubleshooting

### Microphone not working
- Ensure you've granted microphone permission
- Check that no other app is using the microphone
- Try refreshing the page

### Audio file won't play
- Ensure the file is a supported format (MP3, WAV, OGG, AAC)
- Check that the file isn't corrupted
- Try a different file

### Visualization is laggy
- Reduce complexity and symmetry settings
- Close other browser tabs
- Try a different browser

### PWA install prompt not appearing
- Ensure you're using HTTPS (or localhost for development)
- Check that the manifest.json is properly served
- Look for the install icon in the browser's address bar

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

This project is open source. Feel free to use, modify, and distribute as needed.

## Credits

- Inspired by [CymaScope](https://cymascope.com/) research on cymatics
- Based on principles of Chladni patterns and atomic orbital geometry
- Font: [Manrope](https://fonts.google.com/specimen/Manrope) by Mikhail Sharanda

## Changelog

### v1.0.0
- Initial release
- Real-time audio visualization
- Microphone and file input support
- Interactive controls panel
- PWA support with offline caching
- Responsive design for all devices
