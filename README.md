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

1. **Download**: Get the latest release or clone the repo
2. **Install Required Tools**:
   - [MKVToolNix](https://mkvtoolnix.download/)
   - [FFmpeg](https://ffmpeg.org/)
   - [Aegisub](https://aegisub.org/)
3. **Run**:
   - `Muxing Tools GUI.exe` (GUI)
4. **Configure Tools**:
   - If tools are in your PATH, they’re auto-detected
   - Otherwise, set custom paths in Settings → Tools
5. **Start Muxing**:
   - Use the Muxer page to process videos

## Usage

1. **Select Video Source**: Browse for your video files
2. **Scan for Tracks**: Detect internal/external audio and subtitle tracks
3. **Configure Tracks**: Add, reorder, and set properties for tracks
4. **Set Output**: Choose output folder
5. **Start Processing**: Begin batch muxing

## Advanced

- **Presets**: Save and reuse muxing configurations
- **Macros**: Automate repetitive tasks
- **Templates**: Custom file naming with variables (`$show$`, `$ep$`, etc.)
- **Batch Operations**: Process multiple files with the same config
- **Subtitle Tools**: Style replacement, format conversion, smart handling

## Troubleshooting

- Check `App/logs/` for error details
- Verify tool installations and paths
- Run as administrator if you see permission errors
- Use SSD and close other apps for best performance

## Tips

- Backup originals before processing
- Test with a few files first
- Organize tracks in `App/tracks/`
- Use presets and macros for efficiency

## Support

- Review logs for error details
- Verify tool installations and paths
- Test with sample files
- See the Guide page in-app for documentation

---

## Folder Structure

The application uses these folders for organization:

```
App/
├── configs/         # JSON configs, presets, macros, styles
├── logs/            # Application logs
└── tracks/
    ├── audio/       # External audio files
    └── subtitles/   # External subtitle files
---

**Note**: This is a portable application. All settings and configurations are stored locally in the application folder and will persist between sessions.
