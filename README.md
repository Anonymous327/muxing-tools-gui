# Muxer - Portable Executable

**Note:** This project is based on [muxtools](https://github.com/muxtools/muxtools). For more information about muxtools, visit their [documentation](https://muxtools.vodes.pw/).

A portable GUI application for batch video muxing operations with advanced subtitle and audio track management.

## Quick Start

1. **Download**: Download the executable file from the releases
2. **Run the Application**:
   - `Muxing Tools.exe` - Standard GUI version
   - `Muxing Tools - Console.exe` - GUI version with console window visible for debugging
3. **Configure Tools** (Optional):
   - If MKVToolNix, FFmpeg, and Aegisub are in your PATH, they will be detected automatically
   - Otherwise, go to Settings → Tools and set the paths to the required tools
4. **Start Muxing**: Use the Muxer page to process your videos

## Requirements

### Required Tools

- **MKVToolNix**: Download from [mkvtoolnix.download](https://mkvtoolnix.download/)
- **FFmpeg**: Required for audio encoding (download from [ffmpeg.org](https://ffmpeg.org/))
- **Aegisub**: Required for subtitle editing (download from [aegisub.org](https://aegisub.org/))

**Note**: Tools can be used from your system PATH or you can set custom paths in the application settings.

### System Requirements

- Windows 10/11 (64-bit)
- 4GB RAM minimum (8GB recommended)
- 2GB free disk space

## First Time Setup

1. **Install Required Tools**:

   - Download and install MKVToolNix from [mkvtoolnix.download](https://mkvtoolnix.download/)
   - Download and install FFmpeg from [ffmpeg.org](https://ffmpeg.org/)
   - Download and install Aegisub from [aegisub.org](https://aegisub.org/)

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
Muxer/
├── tracks/
│   ├── audio/          # External audio files
│   └── subtitles/      # External subtitle files
├── output/             # Processed output files
├── configs/            # Configuration files
└── logs/              # Application logs
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
