# Cymatics Audio Visualizer - Chrome Extension

A real-time Cymatics visualizer that transforms your music into beautiful geometric sand patterns using GPU-accelerated physics simulation.

## Features

- **High-Fidelity Audio Capture**: Uses Chrome's `tabCapture` API to capture audio directly from your music tabs
- **Realistic Physics**: GPGPU-based particle simulation with 16,384 particles simulating real sand on a vibrating Chladni plate
- **Premium Design**: BOSE-inspired minimalist interface
- **Live Controls**: Adjust colors, frequency response, friction, and pattern complexity in real-time
- **Zero Audio Loss**: Music continues playing normally while being visualized

## Installation

### Step 1: Prepare the Extension

1. Download/extract all extension files to a folder called `cymatics-extension`
2. Make sure you have these files:
   ```
   cymatics-extension/
   ├── manifest.json
   ├── background.js
   ├── popup.html
   ├── popup.js
   ├── visualizer.html
   ├── icon16.png
   ├── icon48.png
   └── icon128.png
   ```

### Step 2: Load in Chrome

1. Open Chrome and go to `chrome://extensions/`
2. Enable **Developer mode** (toggle in top-right corner)
3. Click **"Load unpacked"**
4. Select the `cymatics-extension` folder
5. The Cymatics icon should appear in your extensions toolbar

## Usage

### Basic Usage

1. **Open a music tab** (Spotify, YouTube Music, Apple Music, SoundCloud, etc.)
2. **Start playing music**
3. **Click the Cymatics extension icon** in your toolbar
4. **Click "Start Visualizer"**
5. A new window will open showing the visualizer
6. Your music will continue playing normally!

### Controls

The visualizer includes real-time controls:

- **Plate Color**: Change the background color (the "metal plate")
- **Sand Color**: Change the particle color
- **Frequency Response**: How strongly particles react to audio (0.1-3.0)
- **Friction**: How quickly particles settle (0.8-0.99)
- **Pattern Complexity**: Density of Chladni node patterns (1.0-5.0)

### Tips for Best Results

- **Bass-heavy music** creates large, flowing patterns
- **High-frequency music** (treble) creates intricate, detailed patterns
- **Adjust Frequency Response** higher (2.0-3.0) for subtle music
- **Lower Friction** (0.8-0.9) for more dynamic movement
- **Higher Complexity** (3.0-5.0) creates more intricate geometric patterns

## Supported Music Services

Works with any tab playing audio:
- ✅ Spotify (open.spotify.com)
- ✅ YouTube / YouTube Music
- ✅ Apple Music (music.apple.com)
- ✅ SoundCloud
- ✅ Any other audio-playing website

## Troubleshooting

### "No active capture found"
- Make sure music is actually **playing** in the tab before starting the visualizer
- Refresh the music tab and try again

### Extension icon doesn't appear
- Make sure Developer mode is enabled in `chrome://extensions/`
- Check that all files are in the correct folder
- Try removing and re-loading the extension

### No particles visible
- Check the browser console (Cmd+Option+J) for errors
- Make sure music is playing and audio levels are visible in the tab
- Try increasing the Frequency Response slider

### Audio stopped playing
- This shouldn't happen - audio is automatically routed back to speakers
- If it does, close the visualizer window and restart

## Technical Details

- **Particle System**: 16,384 particles (128×128 GPGPU compute texture)
- **Physics Engine**: Custom GLSL shaders simulating Chladni plate vibrations
- **Audio Processing**: Web Audio API with FFT analysis (256 bins)
- **Rendering**: Three.js with WebGL2
- **Audio Routing**: tabCapture → AudioContext → GainNode → destination (speakers)

## Development

### File Structure

- `manifest.json` - Extension configuration and permissions
- `background.js` - Service worker handling tab capture
- `popup.html/js` - Extension popup UI
- `visualizer.html` - Main visualizer with Three.js and shaders

### Modifying the Physics

The Chladni physics are in the `velocityShader()` function in `visualizer.html`. Key parameters:

```glsl
float chladniPattern(vec2 pos, float freq1, float freq2, float freq3, float freq4) {
    // Modify these values to change pattern characteristics
    float a = uComplexity;
    float b = uComplexity * 1.5;
    // ...
}
```

## Future Features

- [ ] Video recording with audio sync
- [ ] Screenshot/snapshot capture
- [ ] Preset patterns and color schemes
- [ ] Beat detection for reactive patterns
- [ ] Safari extension support (macOS App Store)

## Credits

Built with:
- Three.js (WebGL library)
- Web Audio API
- Chrome Extension APIs

Inspired by the work of Ernst Chladni and Cymatics research.

## License

MIT License - Feel free to modify and distribute!

---

**Enjoy visualizing your music! 🎵✨**
