# Muxing Tools GUI

A portable, advanced GUI for batch video muxing, subtitle/audio management, and automation. Built for Windows, based on [muxtools](https://github.com/Jaded-Encoding-Thaumaturgy/muxtools).

## Features

- Batch muxing for MKV, MP4, AVI, and more
- Advanced subtitle and audio track management
- Preset and macro system for automation
- Custom naming templates
- Drag-and-drop track reordering
- Style replacement, format conversion, smart subtitle processing
- Integrated logs and troubleshooting
- Portable: all configs and logs stored locally

## Quick Start

1. **Download**: Get the latest release from [releases](https://github.com/Anonymous327/muxing-tools-gui/releases)
2. **Install Required Tools**:
   - [MKVToolNix](https://mkvtoolnix.download/) (Can be installed or added to PATH or auto-download)
   - [FFmpeg](https://ffmpeg.org/) (Add to PATH or auto-download)
   - [Aegisub](https://aegisub.org/) (Can be installed or added to PATH or auto-download)
   - [FLACCL](https://github.com/gchudov/cuetools.net/releases/download/v2.2.6/CUETools_2.2.6.zip) (Add to PATH or auto-download)
   - [EAC3to](https://files.catbox.moe/hn9oms.7z) (Add to PATH or auto-download)
   - [qaac](https://pomf2.lain.la/f/u8yyfyed.7z) (Add to PATH or auto-download)
   - [Opusenc](https://www.rarewares.org/files/opus/opus-tools%200.2-34-g98f3ddc-x64.zip) (Add to PATH or auto-download)
   - [FLAC](https://github.com/xiph/flac/releases/download/1.5.0/flac-1.5.0-win.zip) (Add to PATH or auto-download)
   - [WavPack](https://github.com/dbry/WavPack/releases/download/5.8.1/wavpack-5.8.0-x64.zip) (Add to PATH or auto-download)
3. **Run**:
   - `Muxing Tools GUI.exe` (GUI)
4. **Configure Tools**:
   - If tools are in your PATH, they’re auto-detected
   - Otherwise, set custom paths in Settings → Tools
5. **Configure Track Paths (Optional)**:
   - Set custom track paths in Settings → Track Paths
6. **Start Muxing**:
   - Use the Muxer page to process videos

## Troubleshooting

- Check `App/logs/` for error details

## Tips

- Backup originals before processing
- Test with a few files first
- Organize tracks in `App/tracks/`. However, you can also choose your own subtitle and audio directories on the Settings page for more flexibility
- Use presets and macros for efficiency
- Use simple names for audio and subtitle files (S##E##_language; use keywords if you want multiple tracks in the same folder)
- If you want a feature added or an existing feature improved, do let me know

---

## Folder Structure

The application uses these folders for organization:

```
App/
├── binaries/
├── configs/         # JSON configs, presets, macros, styles
├── logs/            # Application logs
└── tracks/
    ├── audio/       # External audio files
    └── subtitles/   # External subtitle files
```

**Note**: This is a portable application. All settings and configurations are stored locally in the application folder and will persist between sessions. Also, I should probably create a more detailed guide at some point.
