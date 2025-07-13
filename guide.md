# Muxing Tools GUI: Complete Guide

This guide provides a comprehensive overview of all pages and features available in the Muxing Tools GUI.

---

## Table of Contents

- [Muxer Page](#muxer-page)
- [Sub Editor Page](#sub-editor-page)
- [Attachment Extractor Page](#attachment-extractor-page)
- [Templates Page](#templates-page)
- [Settings Page](#settings-page)

---

## Muxer Page

The main page for batch muxing operations with comprehensive preset management and audio/subtitle track handling.

### Main Controls

#### Preset Management

- **Preset Dropdown**: Select from saved presets. Each preset contains all your settings for a specific series or project.
- **New Preset**: Create a new blank preset. You'll be prompted to name it.
- **Save Preset**: Save changes to the current preset. Shows an asterisk (\*) when there are unsaved changes.
- **Delete Preset**: Remove the selected preset from your configuration.
- **Open Preset JSON**: Opens the presets.json file in your default text editor for advanced manual editing.

#### Video Source Management

- **Add Source**: Browse and add folders containing your video files. These are the source MKV files you want to process.
- **Remove Source**: Remove the selected source folder from the current preset.
- **Scan for Tracks**: Automatically detect and list all audio and subtitle tracks in your source files. This populates the track lists below.
- **Process Video Range**: Specify which videos to process:
  - Leave empty or type "all" to process all videos
  - Specific episodes: "1, 3, 5" for individual episodes
  - Ranges: "1-5" or "10-12" for episode ranges
  - Complex combinations: "1-3, 5, 10-" (from 10 to the end)
  - Open-ended: "15-" means "from episode 15 to the end"

### Tabs

#### Naming Tab

- **Show Name**: The general series name. Use `$show$` in templates to reference this name.
- **Filename Template**: Template for output filenames. Use variables like `$show$`, `$ep$`, `$title$` to create consistent naming. Includes Add/Edit buttons for template management.
- **MKV Title Template**: Template for the embedded title inside MKV files. This appears in media players. Includes Add/Edit buttons for template management.
- **Manage All Templates...**: Opens the Templates page to edit filename and title templates.
- **Automated Naming**: Configure automatic title fetching and naming:
  - **Configure TMDB...**: Set up automatic episode title fetching from The Movie Database
  - **Configure TVDB...**: Set up automatic naming using The TV Database
  - **Set Custom Titles...**: Manually set sequential titles for episodes when automatic fetching isn't available

#### Premux Tab

Configure advanced muxing options and video track information:

- **Premux mkvmerge Options**: Checkboxes for various mkvmerge flags:
  - `--no-audio`: Exclude audio tracks from the output
  - `--no-video`: Exclude video tracks from the output
  - `--no-subtitles`: Exclude subtitle tracks from the output
  - `--no-buttons`: Exclude button tracks from the output
  - `--no-track-tags`: Exclude track-specific tags from the output
  - `--no-chapters`: Exclude chapter information from the output
  - `--no-attachments`: Exclude attachments (fonts, images) from the output
  - `--no-global-tags`: Exclude global tags from the output
- **Edit Video Track Info**: Configure the primary video track:
  - **Track Name**: Set a custom name for the video track
  - **Language**: Set the language code for the video track (e.g., "eng")
  - **Flags**: Set default/forced track properties
- **Custom mkvmerge Args**: Advanced mkvmerge arguments for the primary video track
- **Preserve original video track name**: Keep the original video track name from the source file

#### Formatting Tab

- **Number Formatting**: Python format specifier for episode numbers. Use "02d" to format episode 1 as "01", "03d" for "001".
- **Apply Space Replacement To**: Choose where to replace spaces - in filenames, titles, or both.
- **Replace Spaces With**: Character to replace spaces with (e.g., "." for dots, "\_" for underscores).

#### Custom Variables Tab

Create custom variables for use in templates with range-based rules:

- **Variable Name**: Create variables like `release_tag`, `group`, etc.
- **Default Value**: The value used when no specific rule applies.
- **Range Rules**: Set specific values for video ranges (e.g., "1-8: GroupA", "9-: GroupB").
- **Usage**: Use `$variable_name$` in any template to reference these variables.

#### Subtitles Tab

- **Generate Chapters from Subtitle Track**: Create chapter markers from a selected subtitle track. Useful for creating scene-based chapters.
- **Resample Subtitles**: Adjust subtitle positioning and sizing to match different video dimensions. Scales subtitle coordinates and font sizes for different video resolutions.
- **SRT to ASS Conversion**: Convert SRT subtitle files to ASS format with proper styling.

#### Signs & Songs Tab

Generate derivative subtitle tracks by removing dialogue styles, leaving only signs and songs:

- **Enable**: Toggle Signs & Songs generation on/off.
- **Base Subtitle Track**: Select the source subtitle track to process.
- **Track Title/Language**: Configure the title and language for the new track.
- **Flags**: Set default/forced track properties for the new track.
- **Dialogue Styles to Remove**: Comma-separated list of styles to exclude (e.g., "Default,Main").
- **Per-track Functions**: Advanced options for processing individual tracks differently.

#### Autoswapper Tab

Generate an "autoswapped" subtitle track with advanced swapping and style options:

- **Enable**: Toggle Autoswapper track generation on/off.
- **Base Subtitle Track**: Select the source subtitle track to use as the base for autoswapping.
- **Track Title/Language**: Set the title and language for the autoswapped track.
- **Flags**: Set default/forced track properties for the new track.
- **Allowed Styles**: Comma-separated list of styles to perform swapping on. Leave blank for all styles.
- **Print Swaps to Log**: If enabled, every swap operation will be printed to the log (useful for debugging).
- **Inline Marker**: Character to use for inline swaps (default: `*`).
- **Line Marker**: Marker for full-line swaps (default: `***`).
- **Inline Tag Markers**: Two characters to be replaced with `{` and `}` in inline swaps for tags. Leave blank to disable tag swapping.
- **Per-track Functions**: Advanced options for processing the autoswapped track (Clean Styles, Shift to 0, Clean Garbage, Clean Comments, Clean Extradata, Collect Fonts).

#### Audio Encoding Tab

Configure audio encoding for selected tracks:

- **Enable Audio Encoding**: Toggle audio encoding on/off for the muxing process.
- **Codec**: Select the audio codec to use for encoding (AAC, Opus, MP3, FLAC, AC3).
- **Tracks to Encode**: Choose which audio tracks to encode. Leave empty to encode all tracks.

---

### Track Management

#### Subtitle Tracks

- **Add Track**: Manually add a new subtitle track with custom settings.
- **Add Scanned...**: Add tracks from the scanned video files to your configuration.
- **Edit/Remove**: Right-click context menu for track management.
- **Drag to Reorder**: Reorder tracks by dragging them in the list.

#### Audio Tracks

- **Add Track**: Manually add a new audio track with custom settings.
- **Add Scanned...**: Add tracks from the scanned video files to your configuration.
- **Edit/Remove**: Right-click context menu for track management.
- **Drag to Reorder**: Reorder tracks by dragging them in the list.

### Output & Processing

- **Output Folder**: Select the destination directory for your muxed files.
- **Start Muxing**: Begin the batch muxing process with all configured settings.
- **Progress Bar**: Real-time progress display with the option to cancel the operation.

---

## Sub Editor Page

The Sub Editor Page provides advanced subtitle editing and processing tools with batch operations. It includes drag-and-drop file management and multiple processing tabs.

### Main Features

#### File Management

- **Drag & Drop Area**: Drag and drop subtitle files (.ass, .ssa, .srt, .sub) or folders directly into the interface
- **Add Files/Folders**: Browse and add individual files or entire folders
- **Clear List**: Remove all files from the processing list
- **Convert SRT/SUB to ASS**: Convert subtitle files to ASS format with proper styling

#### Top-Level Actions

- **Remove Unused Styles**: Clean up unused styles, fonts, and elements from subtitle files
- **Run SmartQuotify**: Convert quotes to proper typographic quotes with settings
- **Run GJM Restyle**: Apply GJM-specific styling to subtitle files
- **Convert British to American English**: Convert British English spelling to American English

### Processing Tabs

#### Formatting Tab

- **Remove Aegisub Project Garbage section**: Clean up Aegisub project metadata
- **Remove auto-generated script comments**: Remove automatic comments from subtitle files
- **Script Info Title**: Choose how to handle script titles (Keep Original, Use Filename, Clear Title)
- **Run Formatting**: Execute the formatting operations on selected files

#### Resample Tab

- **Target Resolution**: Select target resolution for subtitle scaling (360p to 2160p)
- **Run**: Execute subtitle resampling to match the selected video dimensions
- **What it does**: Scales subtitle positioning and sizing to match the target video resolution, adjusting subtitle coordinates and font sizes for different video dimensions

#### Unfuck CR Tab

- **Settings**: Configure Unfuck CR processing parameters
- **Run Unfuck CR**: Execute the Unfuck CR script on selected files

#### Split Overlap Tab

- **Line to treat as second speaker**: Choose which part of split lines to treat as second speaker
  - Second part (after \N)
  - First part (before \N)
- **Run Split**: Execute the split overlap operation

### Style Management

#### Presets Section

- **Preset Dropdown**: Select from saved style presets
- **New Preset**: Create a new style preset
- **Save Preset**: Save current settings as a preset
- **Delete Preset**: Remove the selected preset

#### Batch Style Replacement Rules

- **Load Styles**: Extract styles from selected files for replacement rules
- **Add Rule**: Create new style replacement rules
- **Remove Selected**: Remove selected style rules
- **Clear All Rules**: Remove all style replacement rules
- **Run Batch Style Replacements**: Execute style replacements on selected files

### Settings and Configuration Dialogs

The Sub Editor Page includes several advanced settings dialogs for fine-tuning processing:

#### Unfuck CR Settings Dialog

- **Access:** Click the "Settings..." button in the Unfuck CR tab.
- **Options:**
  - Default Style
  - Keep Flashback Styles
  - Dialogue Styles (comma-separated)
  - Top Styles (comma-separated)
  - Italics Styles (comma-separated)
  - Alt Style for Overlap
  - Alt Style Identifiers (comma-separated)
  - Auto-import styles from loaded files

#### SmartQuotify Settings Dialog

- **Access:** Click the gear/settings icon next to the "Run SmartQuotify" button.
- **Options:**
  - Enable quote conversion (choose style: curly, straight, or custom)
  - Custom opening/closing quote characters
  - Enable apostrophe conversion (choose style or custom, add warning)
  - Enable dash and ellipsis conversion (choose dash style or custom, enable ellipsis)
  - Context-aware processing (skip styles, preserve effects, smart detection)

#### Convert to ASS Dialog

- **Access:** Click the "Convert SRT/SUB to ASS..." button at the top of the page.
- **Options:**
  - Drag-and-drop SRT/SUB files for conversion
  - Select a Style Rule Preset
  - Set PlayResX/PlayResY (target resolution)
  - Choose output directory

#### Add/Edit Style Replacement Dialog

- **Access:** In the batch style replacement section, click Add/Edit rule.
- **Options:**
  - Old/New style name
  - Font, colors (primary, secondary, outline, shadow)
  - Scale X/Y, spacing, angle
  - Border style, alignment
  - Margins (L/R/V), outline width, shadow depth
  - Encoding
  - Preset management for style replacements

---

## Attachment Extractor Page

Extracts various components from MKV files in batch using MKVToolNix tools.

### Extraction Options

- **Audio**: Extract audio tracks from MKV files
- **Subtitles**: Extract subtitle tracks from MKV files
- **Attachments**: Extract embedded files (fonts, images, etc.) from MKV files
- **Chapters**: Extract chapter information from MKV files
- **Tags**: Extract metadata tags from MKV files
- **Cues**: Extract cue information for precise seeking
- **Timestamps**: Extract timestamp data for each track

### File Management

- **Drag & Drop Area**: Drag and drop MKV files or folders directly into the interface
- **Add Videos**: Browse and add individual MKV files
- **Clear List**: Remove all files from the processing list

### Output Configuration

- **Output Folder**: Select the base directory where extracted files will be saved
- **Browse Output**: Browse to select the output directory
- **Start Extraction**: Begin the batch extraction process

### Logging

- **Log Area**: Real-time display of extraction progress and results

---

## Templates Page

Manage filename and title templates for all presets with advanced variable support.

### Template Management

- **Preset Selection**: Choose which preset to edit templates for
- **Template Types**: Filename templates and MKV title templates
- **Add Template**: Create new templates with custom names
- **Edit Template**: Modify existing templates
- **Delete Template**: Remove unused templates
- **Copy Templates**: Duplicate templates between presets

### Template Variables

- **Standard Variables**: `$show$`, `$ep$`, `$season$`, `$videostem$`
- **TMDB Variables**: `$title$`, `$title_sanitized$` (when TMDB enabled)
- **TVDB Variables**: `$seriesname$`, `$episodename$`, etc. (when TVDB enabled)
- **Custom Variables**: User-defined variables from presets

### Template Examples

- **Filename**: `$show$ - S01E$ep$ - $title$.mkv`
- **MKV Title**: `$show$ - Episode $ep$`
- **Custom**: `$show$_$release_tag$_E$ep$.mkv`

### Advanced Features

- **Variable Preview**: See how your template will look with actual values
- **Template Validation**: Check for syntax errors in your templates
- **Import/Export**: Share templates between different installations

### Add/Edit Template Dialog

The Add/Edit Template dialog provides a streamlined way to create or modify filename and MKV title templates for your presets.

**Key Features:**

- **Existing Template Dropdown:**  
  At the top, a dropdown lets you quickly load any previously created template string from any preset.

  - **Deduplication:** Only unique template strings are shown (even if they have different names or come from different presets).
  - **Context:** Each entry shows the template name, string, preset, and type for clarity.
  - **Capped List:** The dropdown shows up to 15 items at once for easy browsing.

- **Auto-Fill:**  
  Selecting a template from the dropdown will auto-fill the name and string fields, allowing you to reuse or modify templates efficiently.

- **Clear Form Button:**  
  Instantly clears the name and string fields and resets the dropdown.

- **Variable Buttons:**  
  Below the template string field, you’ll find organized buttons for all available variables (Standard, TMDB, TVDB). Click any button to insert the variable at the cursor position in your template.

- **Compact Layout:**  
  The dialog is designed for quick, efficient template editing, with minimal spacing and a clear, modern look.

---

**Tip:**  
Use the dropdown to quickly reuse or adapt templates you’ve used in other presets, ensuring consistency and saving time.

---

## Settings Page

Configure application-wide settings that affect all pages and operations.

### Personalization Settings

#### Theme Color

- **Theme Color Picker**: Change the theme color of your application
- **Interface Zoom**: Adjust the size of widgets and fonts (100% to 200% or system setting)

### Tool Paths Configuration

#### MKVToolNix Directory

- **Purpose**: Specify the path to your MKVToolNix installation
- **What it does**: The application uses MKVToolNix tools (mkvmerge, mkvinfo, etc.) for muxing operations
- **How to set**: Browse to the folder containing mkvmerge.exe

#### Aegisub Directory

- **Purpose**: Specify the path to your Aegisub installation
- **What it does**: Used for subtitle editing and processing tasks
- **How to set**: Browse to the folder containing Aegisub.exe

#### FFMPEG Directory

- **Purpose**: Specify the path to your FFmpeg installation
- **What it does**: Used for audio encoding, subtitle conversion, and other media processing tasks
- **How to set**: Browse to the folder containing ffmpeg.exe

### Settings Management

- **Auto-save**: Settings are automatically saved when changed
- **Success Notifications**: Confirmation messages when settings are updated

---

## Template Variables Reference

### Standard Variables

| Variable      | Description                   | Example            |
| ------------- | ----------------------------- | ------------------ |
| `$show$`      | Show name from preset         | `My Awesome Anime` |
| `$ep$`        | Episode number (formatted)    | `01`               |
| `$season$`    | Season number (formatted)     | `01`               |
| `$videostem$` | Video filename (no extension) | `Episode1`         |
| `$crc32$`     | CRC32 checksum of final file  | `A1B2C3D4`         |

### TMDB Variables (when enabled)

| Variable            | Description                   |
| ------------------- | ----------------------------- |
| `$title$`           | Original episode/movie title  |
| `$title_sanitized$` | Sanitized title for filenames |

### TVDB Variables (when enabled)

| Variable           | Description                |
| ------------------ | -------------------------- |
| `$seriesname`      | Sanitized series name      |
| `$episodename`     | Sanitized episode name     |
| `$seriesname_raw`  | Original series name       |
| `$episodename_raw` | Original episode name      |
| `$seasonnumber`    | Zero-padded season number  |
| `$episodenumber`   | Zero-padded episode number |
| `$ext`             | File extension             |
| `$crc32`           | CRC32 Hash (if enabled)    |

### Custom Variables

Any variable created in the Custom Variables tab can be used as `$variable_name$` in templates.

---

## Tips and Best Practices

### Preset Management

- Create separate presets for different series or projects
- Use descriptive preset names for easy identification
- Save presets frequently to avoid losing work
- Export/import presets for backup or sharing

### Template Design

- Use descriptive template names
- Test templates with a few files before batch processing
- Consider file system limitations when designing filenames
- Use custom variables for project-specific information

### Audio/Subtitle Track Organization

- Use consistent naming conventions for tracks
- Leverage the "Add Scanned" feature for efficiency
- Test track configurations with sample files
- Use the drag-and-drop reordering for optimal track order

---

This guide covers all major features and functionality of the Muxing Tools GUI. For additional help or feature requests, refer to the project documentation or create an issue on the project repository.
