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

**Note:** This is a portable app. All settings/configs are stored locally and persist between sessions.

2. **Configure Tool Paths** (Optional):

   - If tools are in your system PATH, the application will find them automatically
   - To use custom paths, open the application and go to Settings → Tools
   - Set custom paths for MKVToolNix, FFmpeg, and Aegisub if needed

3. **Create Your First Preset**:
   - Go to the Muxer page
   - Click "New Preset" to create your first configuration
   - Save the preset with a descriptive name

## Basic Usage

### Step 1: Select Video Source

- Click "Browse" to select a folder containing your video files
- The application will scan for supported video formats (MKV, MP4, AVI, etc.)

### Step 2: Scan for Tracks

- Click "Scan Video Source" to identify internal audio and subtitle tracks
- Review the detected tracks in the lists

### Step 3: Configure Tracks

- **Add Audio Tracks**: Click "Add Audio Track" to add external audio files
- **Add Subtitle Tracks**: Click "Add Subtitle Track" to add external subtitle files
- **Reorder Tracks**: Drag and drop tracks to change their order
- **Configure Properties**: Right-click tracks to set language, default, forced flags

### Step 4: Set Output

- Click "Select Output" to choose where processed files will be saved
- The application will create the output folder if it doesn't exist

### Step 5: Start Processing

- Click "Start Muxing" to begin batch processing
- Monitor progress in the terminal output
- Cancel at any time with the "Cancel" button

## Advanced Features

### Template System

- Create custom naming templates using variables like `$show$`, `$ep$`, `$title$`
- Access templates from the Templates page or Manage All Templates button
- Use custom variables for project-specific information

### Track Management

- **Drag and Drop**: Reorder tracks by dragging them in the lists
- **External Files**: Add subtitle and audio files from your `tracks` folder
- **Auto-Scanning**: Automatically find matching tracks based on keywords
- **Batch Operations**: Process multiple files with the same track configuration

### Subtitle Processing

- **Style Replacement**: Replace subtitle styles automatically
- **Format Conversion**: Convert between subtitle formats
- **Smart Processing**: Handle signs, songs, and other special content

## Folder Structure

The application uses these folders for organization:

```
App/
├── configs/         # JSON configs, presets, macros, styles
├── logs/            # Application logs
└── tracks/
    ├── audio/       # External audio files
    └── subtitles/   # External subtitle files
```

## Troubleshooting

### Common Issues

**"MKVToolNix not found"**

- Ensure MKVToolNix is installed
- Check the tool path in Settings → Tools
- Verify the installation directory contains `mkvmerge.exe`

**"Permission denied" errors**

- Run the application as administrator
- Check file permissions on input/output directories
- Ensure antivirus software isn't blocking the application

**Performance issues**

- Close other applications to free up memory
- Process files in smaller batches
- Use SSD storage for better I/O performance

### Getting Help

1. Check the logs in the `logs` folder for detailed error information
2. Verify all required tools are properly installed and configured
3. Test with sample files before large batches
4. Review preset configurations for errors

## Tips

- **Backup First**: Always backup your original files before processing
- **Test Small**: Test with 1-2 files before large batches
- **Organize Files**: Keep your audio/subtitle files organized in the `tracks` folder
- **Use Presets**: Save your configurations as presets for reuse
- **Monitor Logs**: Check the logs for detailed processing information

## Support

For issues and questions:

- Check the logs for error details
- Verify tool installations and paths
- Test with sample files
- Review the Guide page in the application for detailed documentation

---

**Note**: This is a portable application. All settings and configurations are stored locally in the application folder and will persist between sessions.
