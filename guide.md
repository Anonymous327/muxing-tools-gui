# Muxing Tools GUI: Complete Guide

This guide provides a comprehensive overview of all pages and features available.

---

## Table of Contents

- [Muxer Page](#muxer-page)
- [Sub Editor Page](#sub-editor-page)
- [MKV Extractor Page](#mkv-extractor-page)
- [Logs Page](#logs-page)
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
- **Filename Template**: Template for output filenames. Use variables like `$show$`, `$ep$`, `$title$` to create consistent naming. Available templates include:
  - **Default**: `$videostem$` (uses the original video filename)
  - **Default (TMDB)**: `$show$ - S$season$E$ep$ - $title_sanitized$` (TMDB-compatible naming)
  - **Default (TVDB)**: `$seriesname$ - S$seasonE$episodenumber - $episodename$ext` (TVDB-compatible naming)
  - Includes Add/Edit buttons for template management
- **MKV Title Template**: Template for the embedded title inside MKV files. This appears in media players. Available templates include:
  - **No Title**: (empty - no embedded title)
  - **Default (TMDB)**: `$show$ - S$seasonE$ep$ - $title$` (TMDB episode format)
  - **Default (TVDB)**: `$seriesname$ - S$seasonE$episodenumber - $episodename` (TVDB episode format)
  - Includes Add/Edit buttons for template management
- **Manage All Templates...**: Opens the Templates page to edit filename and title templates.
- **Automated Naming**: Configure automatic title fetching and naming:
  - **Configure TMDB...**: Set up automatic episode title fetching from The Movie Database
  - **Configure TVDB...**: Set up automatic naming using The TV Database
  - **Set Custom Titles...**: Manually set sequential titles for episodes when automatic fetching isn't available

---

### Using the TMDB, TVDB, and Custom Titles Dialogs

#### TMDB Dialog (Configure TMDB...)

This dialog allows you to fetch episode titles and metadata from The Movie Database (TMDB).

**Fields and Options:**

- **Enable TMDB Integration**: Toggle TMDB metadata fetching on or off.
- **This is a Movie (not a TV series)**: Check if muxing a movie instead of a TV show.
- **TMDB ID**: Enter the numeric TMDB ID for the show or movie. You can find this on the TMDB website.
- **Season Number**: For TV shows, specify the season to fetch episode data from.
- **Episode Number Offset**: Add this number to the episode number parsed from the filename (useful for specials or split seasons).
- **Episode Order**: Choose the episode order (Aired, DVD, Absolute, etc.).
- **Language**: Set the language code (e.g., `en-US`, `de`).
- **Use episode number from filename**: If checked, the episode number is parsed from the filename; otherwise, uses the file’s position in the list.
- **Metadata Options**: Choose which metadata to write (title, IDs, release date, cover art, series summary, episode synopsis).
- **Replace Spaces In Title With**: Replace spaces in titles with a custom character (e.g., `.` or `_`).
- **Title Sanitization Rules**: Add rules to replace or remove specific characters from titles.

**Tips:**

- If you get no results, double-check the TMDB ID and season number.
- Use the language code that matches your preferred episode titles.

---

#### TVDB Dialog (Configure TVDB...)

This dialog allows you to fetch episode titles and metadata from The TV Database (TVDB).

**Fields and Options:**

- **Enable TVDB Integration**: Toggle TVDB metadata fetching on or off.
- **API Key**: Enter your TVDB v4 API key. You can get this from your TVDB account.
- **Show ID**: Enter the numeric TVDB show ID (found in the TVDB URL for the show).
- **Season Number**: Specify the season to fetch episode data from.
- **Episode Number Offset**: Add this number to the episode number parsed from the filename.
- **Metadata Options**: Choose which metadata to write (episode title, IDs, release date, cover art, episode summary, series summary).

**Tips:**

- You must have a valid TVDB API key. If you get errors, check your key and show ID.
- If cover art is not appearing, ensure "Download & Embed Cover Art" is enabled and you are connected to the internet.
- Use the correct season number for the episodes you are muxing.
- **Note:** The TVDB integration only supports the aired order for episodes. DVD, absolute order, and director's cut are not supported.

**Example TVDB Template Usage:**

- **Basic naming**: `$seriesname - S$season$E$ep$ - $episodenameext`
- **With air date**: `$seriesname ($airyear) - S$season$E$ep$ - $episodenameext`
- **Anime format**: `$seriesname - $absolutenumber - $episodenameext`
- **With network**: `[$seriesnetwork] $seriesname - S$season$E$ep$ - $episodenameext`
- **Detailed**: `$seriesname - S$season$E$ep$ - $episodename [$seriesgenres]$ext`

---

#### Custom Titles Dialog (Set Custom Titles...)

This dialog lets you manually specify a list of titles for each episode or file, overriding automatic fetching.

**How to Use:**

- **MKV Titles Tab**: Enter one MKV title per line. These will be applied in order to the muxed files.
- **Filename Titles Tab**: Enter one filename episode value per line. These will replace `$ep$` in the filename template sequentially.

**Tips:**

- Use this if TMDB/TVDB does not have the correct episode titles or you want custom naming.
- The order of lines matters: the first line is used for the first file, the second for the second, etc.
- Leave a line blank to skip a title for that episode.

---

**Troubleshooting:**

- If metadata is not being applied, ensure the integration is enabled and all required fields (API keys, IDs) are filled in.
- For cover art issues, check your internet connection and that the cover art option is enabled.
- If custom titles are not appearing, make sure the dialog is saved and the preset is updated.

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
  - **Language**: Set the language code for the video track (e.g., "en")
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
  - **Configure Settings**: Click the gear icon to open the Chapter Generation Settings dialog
  - **Chapter Detection Settings**: Configure how chapters are detected in subtitle files
    - **Marker Keywords**: Comma-separated list of keywords to search for (e.g., "chapter, chptr, episode, part")
    - **Use Actor Field for Detection**: Search for chapter markers in the actor/character field instead of the effect field
    - **Print Found Chapters to Log**: Log all detected chapters for verification
  - **File Encoding**: Set the character encoding for reading subtitle files (default: utf_8_sig)
  - **Advanced Time Settings**: Configure timestamp interpretation for muxtools compatibility
    - **Time Source Override**: Override the source of timestamps (advanced setting)
    - **Time Scale Override**: Override the unit of time for frame timestamps (advanced setting)
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

- **Drag & Drop Area**: Drag and drop ASS subtitle files or folders directly into the interface
- **Add Files/Folders**: Browse and add individual files or entire folders
- **Clear List**: Remove all files from the processing list
- **Convert SRT/SUB to ASS**: Convert subtitle files to ASS format with proper styling

**Note**: The drag and drop area now only accepts ASS files (.ass) to streamline the subtitle editing workflow and ensure compatibility with ASS-specific processing features.

#### Top-Level Actions

- **Remove Unused Styles**: Clean up unused styles, fonts, and elements from subtitle files
- **Run Smarten Punctuation**: Convert quotes to proper typographic quotes with settings
- **Run GJM Restyle**: Apply GJM-specific styling to subtitle files
- **Convert British to American English**: Convert British English spelling to American English
- **Script Property Editor...**: Edit script properties and metadata for selected subtitle files

### Macro Operations

The Sub Editor includes a powerful macro system for automating complex subtitle processing workflows.

#### Macro Features

- **Macro Selection**: Choose from saved macros to run on your files
- **Run Macro**: Execute the selected macro on all selected subtitle files
- **Edit Macro**: Modify existing macros or create new ones
- **Delete Macro**: Remove unwanted macros
- **Macro Settings**: Global settings for macro operations

#### Available Macro Operations

Macros can combine any of these operations in sequence:

- **Format Clean**: Clean up formatting, remove unwanted characters, and set script info title
- **Spelling Conversion**: Convert between different spelling systems (e.g., US/UK)
- **Smarten Punctuation**: Convert straight quotes to curly quotes intelligently
- **Resample**: Resample subtitles to different resolutions
- **GJM Restyle**: Apply GJM-specific style transformations
- **Style Merger**: Merge and normalize subtitle styles
- **Remove Unused Styles**: Remove style definitions that aren't used in the file
- **Split Overlap**: Split overlapping subtitle lines

#### Creating Macros

1. Click the settings icon next to the macro controls
2. In the Macro Settings dialog, click "Add Macro"
3. Name your macro and add operations in the desired order
4. Configure settings for each operation as needed
5. Save the macro for reuse

#### Macro Benefits

- **Consistency**: Apply the same processing steps to multiple files
- **Efficiency**: Automate repetitive subtitle editing tasks
- **Customization**: Create workflows tailored to your specific needs
- **Batch Processing**: Process multiple files with complex operations in one click

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

#### Style Merger Tab

- **Settings**: Configure Style Merger processing parameters
- **Run Style Merger**: Execute the Style Merger script on selected files

#### Split Overlap Tab

Split dialogue lines that contain two speakers separated by dashes into overlapping subtitle events.

- **What it does**: Detects subtitle lines formatted like `"- Speaker 1 text\N- Speaker 2 text"` and splits them into two overlapping dialogue events for better presentation of simultaneous speech.

- **Pattern Detection**: Looks for lines with the specific format:

  - Starts with a dash (`-`) followed by first speaker's text
  - Contains `\N` (line break)
  - Followed by another dash (`-`) and second speaker's text
  - Preserves formatting tags like `{\i1}` at the start of each speaker's line

- **Line to treat as second speaker**: Choose which part gets the "Alt" style:

  - **Second part (after \N)**: The text after `\N` gets the Alt style (different color)
  - **First part (before \N)**: The text before `\N` gets the Alt style

- **Style Creation**: Automatically creates an "Alt" style if it doesn't exist:

  - Based on the original line's style
  - Uses custom colors: white text, red secondary, brown outline, transparent shadow
  - Applied to the designated second speaker

- **Timing**: Both lines use the same start and end times (true overlapping dialogue)

- **Use Cases**:

  - Converting single lines with dual speakers into proper overlapping dialogue
  - Creating visually distinct speakers in simultaneous conversations
  - Improving readability of back-and-forth dialogue

- **Run Split**: Execute the split overlap operation on all selected files

**Example**: A line like `"- Hello there!\N- How are you?"` becomes:

- Line 1: `"Hello there!"` (original style)
- Line 2: `"How are you?"` (Alt style with different colors)
- Both lines have identical timing (true overlap)

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

#### Style Merger Settings Dialog

- **Access:** Click the "Settings..." button in the Style Merger tab.
- **Options:**
  - Default Style
  - Keep Flashback Styles
  - Dialogue Styles (comma-separated)
  - Top Styles (comma-separated)
  - Italics Styles (comma-separated)
  - Alt Style for Overlap
  - Alt Style Identifiers (comma-separated)
  - Auto-import styles from loaded files

#### Smarten Punctuation Settings Dialog

- **Access:** Click the gear/settings icon next to the "Run Smarten Punctuation" button.
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

#### Script Property Editor Dialog

- **Access:** Click the "Script Property Editor..." button at the top of the page.
- **Features:**
  - **File Selection**: Choose which file to edit from a dropdown (when multiple files selected)
  - **Batch Mode**: Apply changes to all selected files at once
  - **Standard Fields**: Edit common subtitle properties:
    - Title, Original script, Translation, Editing, Timing
    - Synch point, Updated by, Update details
    - PlayResX/PlayResY (video resolution)
    - YCbCr Matrix (color space)
    - Wrap Style (text wrapping behavior)
    - Scale Border and Shadow (boolean option)
  - **Custom Fields**: Add, edit, or remove custom script properties
  - **Selective Updates**: Choose which fields to update (checkboxes for each field)
  - **Field Management**: Add new custom fields or remove existing ones

**Usage Tips:**

- Use batch mode to apply the same properties to multiple subtitle files
- Custom fields allow storing project-specific metadata
- PlayResX/PlayResY should match your target video resolution
- YCbCr Matrix should match your video's color space for accurate colors

---

## MKV Extractor Page

Extracts various components from MKV files in batch using MKVToolNix tools.

### Extraction Options

Select what to extract from MKV files:

- **Audio**: Extract audio tracks from MKV files
- **Subtitles**: Extract subtitle tracks from MKV files
- **Attachments**: Extract embedded files (fonts, images, etc.) from MKV files
- **Chapters**: Extract chapter information from MKV files as XML
- **Tags**: Extract metadata tags from MKV files as XML
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

### Settings Persistence

Extraction settings (selected options and output directory) are automatically saved and restored when you reopen the application.

### Logging

- **Log Area**: Real-time display of extraction progress and results
- Shows detailed information about which files are being processed
- Reports any errors during the extraction process

---

## Logs Page

View and manage application logs with advanced filtering and display options.

### Log Display Features

- **Real-time Updates**: Automatically refresh log content as new entries are added
- **Color-coded Entries**: Different colors for DEBUG, INFO, WARNING, ERROR, and CRITICAL messages
- **Word Wrap**: Toggle word wrapping for long log lines
- **Auto-scroll**: Automatically scroll to the bottom as new log entries appear
- **Monospace Font**: Clear, readable display of log data

### Log Filtering

- **Level Filter**: Show only specific log levels (All, DEBUG, INFO, WARNING, ERROR, CRITICAL)
- **Refresh**: Manually reload the log file content
- **Clear**: Empty the log file and display area

### Controls

- **Realtime**: Enable/disable automatic log updates
- **Word Wrap**: Toggle line wrapping for better readability
- **Auto-scroll**: Keep the display scrolled to the latest entries
- **Level**: Filter logs by severity level

### Usage Tips

- Use the level filter to focus on specific types of messages
- Enable realtime updates to monitor application activity
- Clear logs periodically to maintain performance
- Word wrap helps with viewing long log lines

---

## Guide Page

View this comprehensive user guide within the application. The Guide Page displays the complete documentation in an easy-to-read format with navigation support.

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
- **TVDB Variables**: `$seriesname$`, `$episodename`, etc. (when TVDB enabled)
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

### Track Paths Configuration

#### Audio Directory

- **Purpose**: Specify where audio track files are stored and accessed
- **Default**: `{base_directory}/App/tracks/audio`
- **What it does**: Sets the default location for browsing audio tracks in the Muxer page
- **How to set**: Browse to select your preferred audio tracks directory

#### Subtitle Directory

- **Purpose**: Specify where subtitle track files are stored and accessed
- **Default**: `{base_directory}/App/tracks/subtitles`
- **What it does**: Sets the default location for browsing subtitle tracks in the Muxer page
- **How to set**: Browse to select your preferred subtitle tracks directory

**Note**: Both audio and subtitle directories can be set independently, allowing you to organize your media files in different locations based on your workflow.

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

| Variable                   | Description                                  |
| -------------------------- | -------------------------------------------- |
| `$seriesname`              | Sanitized series name                        |
| `$episodename`             | Sanitized episode name                       |
| `$seriesname_raw`          | Original series name                         |
| `$episodename_raw`         | Original episode name                        |
| `$seasonnumber`            | Zero-padded season number                    |
| `$episodenumber`           | Zero-padded episode number                   |
| `$ext`                     | File extension                               |
| **Muxtools Compatibility** |                                              |
| `$season$`                 | Zero-padded season number (muxtools format)  |
| `$ep$`                     | Zero-padded episode number (muxtools format) |
| **Extended TVDB Data**     |                                              |
| `$episodeoverview`         | Episode synopsis (sanitized)                 |
| `$episodeoverview_raw`     | Episode synopsis (original)                  |
| `$seriesoverview`          | Series summary (sanitized)                   |
| `$seriesoverview_raw`      | Series summary (original)                    |
| `$airdate`                 | First aired date (YYYY-MM-DD)                |
| `$airyear`                 | Year from air date                           |
| `$airmonth`                | Month from air date (01-12)                  |
| `$airday`                  | Day from air date (01-31)                    |
| `$seriesid`                | TVDB series ID                               |
| `$episodeid`               | TVDB episode ID                              |
| `$absolutenumber`          | Absolute episode number (for anime)          |
| `$dvdepisodenumber`        | DVD episode number                           |
| `$dvdseasonnumber`         | DVD season number                            |
| `$episoderuntime`          | Episode runtime in minutes                   |
| `$seriesrating`            | Series content rating                        |
| `$serieslanguage`          | Primary series language                      |
| `$seriesnetwork`           | Original broadcast network                   |
| `$seriesstatus`            | Series status (Continuing, Ended, etc.)      |
| `$seriesgenres`            | Series genres (comma-separated)              |
| `$episodeguests`           | Guest stars for episode                      |
| `$episodedirectors`        | Episode directors                            |
| `$episodewriters`          | Episode writers                              |
| `$crc32`                   | CRC32 Hash (if enabled)                      |

### Custom Variables

Any variable created in the Custom Variables tab can be used as `$variable_name$` in templates.
