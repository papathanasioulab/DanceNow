# 🎯 Fiji DanceNow Plugin

[![Fiji](https://img.shields.io/badge/Fiji-ImageJ-green.svg)](https://fiji.sc/)
[![Java](https://img.shields.io/badge/Java-8%2B-blue.svg)](https://www.java.com/)

A powerful Fiji/ImageJ plugin that provides a persistent navigation window for precise coordinate jumping with zoom preservation, advanced position management, and visual center indication.

## Features

### Core Navigation
- **Persistent Navigation Window**: A floating, always-on-top window that stays open for repeated use
- **Real-time Position Updates**: Shows your current view center and image information updated every 50ms
- **Zoom Preservation**: Maintains your current zoom level during navigation
- **Visual Center Indicator**: Optional green crosshair showing exact center position for accurate position marking
- **Mouse-Only Interface**: All interactions through mouse clicks (keyboard shortcuts disabled for better integration)

### Position Management
- **Row Numbers**: Automatic row numbering for easy position reference
- **Position List with Notes**: Save positions with optional notes for easy identification
- **In-Table Editing**: Edit positions directly in the table with automatic validation
- **Duplicate Detection**: Automatic warning when adding duplicate X,Y,Z,T positions with option to override
- **Smart Position Adding**: Automatically fills first empty row instead of appending
- **Sorting**: Click column headers to sort by position or note (row numbers maintained)
- **Clear All**: Quick removal of all positions with confirmation dialog
- **Auto-Rename on Export**: Prevents file overwrites by auto-numbering duplicates

### Snapshot Feature (New)
- **Batch Image Capture**: Take snapshots of all positions in your list with one click
- **Customizable Area**: Set snapshot dimensions (default 200x200 pixels)
- **Channel Selection**: Choose which channels to include in multi-channel images (Ch1-Ch4)
- **Annotation Options**:
  - Add position number and note as text overlay (yellow text, top-left)
  - Include center crosshair marker (5px green cross)
  - Horizontal flip option for reversed images
- **Smart Naming**: Saves as `Position_001.png` or `Position_reverse_001.png` for flipped images
- **Progress Tracking**: Real-time progress bar during batch processing
- **Auto CSV Export**: Automatically saves positions.csv alongside snapshots

## 📦 Installation

1. **Download** the latest `DanceNow.jar` from [Releases](https://github.com/ttsunglin/DanceNow/releases) or build from source
2. **Copy** the JAR file to your Fiji installation:
   - Windows: `Fiji.app/plugins/EveryBody/`
   - macOS: `/Applications/Fiji.app/plugins/EveryBody/`
   - Linux: `~/Fiji.app/plugins/EveryBody/`
3. **Restart** Fiji
4. **Access** via menu: `Plugins > EveryBody > DanceNow`

## 🚀 Quick Start

1. **Open** any image in Fiji (2D, 3D stack, or 4D time series)
2. **Launch** DanceNow: `Plugins > EveryBody > DanceNow`
3. **Navigate** using the compact floating window:
   - ✅ Enter coordinates and click "Go"
   - ✅ Toggle green crosshair with "Show center +"
   - ✅ Add current position with "Add" button
   - ✅ Navigate saved positions with Back/Next
   - ✅ Right-click for context menu options

### Basic Navigation
- Enter X,Y,Z,T coordinates in the compact input fields (uniform 3-character width)
- Click "Go" button to navigate (Enter key disabled)
- The view will center on the specified position while preserving zoom
- Toggle "Show center +" to display/hide the green crosshair indicator
- Compact window design optimized for screen space

### Position List Management

#### Adding Positions
- Click **"Add"** to add the current view center position to the list
- Optional **Note field** persists after adding for rapid annotation
- **Right-click** on the position list and select "Paste Positions" from context menu
- Positions are displayed in X,Y,Z,T format with optional notes
- Edit positions directly in the table - changes are validated immediately
- First empty row is automatically used when adding new positions

#### Navigating Through Positions
- Click **"< Back"** to go to the previous position in the list
- Click **"Next >"** to go to the next position in the list
- Click any position in the list to select it, then click "Go"
- Navigation wraps around (Next from last position goes to first)
- Out-of-bounds positions show warnings and prevent navigation
- Manual edits in table are immediately reflected in navigation

#### Managing the List
- Select a position and click **"Remove"** to delete it from the list
- Click **"Clear All"** to remove all positions (with confirmation)
- Click **"Snapshot"** to capture images at all positions with custom settings
- Click **"Export"** to save positions as TXT or CSV format
- Click **"Load"** to import positions from TXT or CSV files
- **Sort positions**: Click column headers to sort by position or note
- **Paste positions via context menu**:
  - Right-click and select "Paste Positions"
  - Supports multiple delimiters: comma, space, or tab
  - Perfect for copying data directly from spreadsheets
  - Format: One position per line with optional note

### 📷 Using the Snapshot Feature

The Snapshot feature allows you to automatically capture images at all saved positions:

1. **Click "Snapshot"** button to open the settings dialog
2. **Configure capture settings**:
   - **Snapshot Area**: Set width and height (default 200x200 pixels)
   - **Include center cross**: Adds a small green crosshair at center
   - **Horizontal reverse**: Flips images horizontally
   - **Annotation text**: Overlays position number and note on image
   - **Channel Selection**: Choose which channels to include (Ch1-Ch4)
3. **Click "Take Snapshots"** and select save directory
4. **Images are saved as**:
   - Normal: `Position_001.png`, `Position_002.png`, etc.
   - Reversed: `Position_reverse_001.png`, `Position_reverse_002.png`, etc.
5. **Automatic CSV export**: Saves `positions.csv` with all position data

### ✨ Key Features

| Feature | Description |
|---------|-------------|
| 🎯 **Smart Crosshair** | Green center indicator that scales with zoom |
| 📝 **Position Notes** | Add descriptions to saved positions |
| 🔄 **Real-time Updates** | 50ms refresh rate for smooth tracking |
| 📷 **Batch Snapshots** | Capture all positions with custom settings |
| 🏷️ **Row Numbers** | Automatic numbering for easy reference |
| ⚠️ **Duplicate Warning** | Alerts when adding duplicate positions |
| 💾 **Auto-save Names** | Never overwrite files - auto-adds (2), (3)... |
| 📊 **CSV/TXT Export** | Full format support with headers |
| 🖱️ **Mouse-Only Mode** | No keyboard shortcuts for better integration |
| ⚡ **Instant Validation** | Immediate feedback on coordinate bounds |
| 🔢 **Smart Sorting** | Click headers to sort by position or note |
| 🖼️ **Annotation Text** | Add position number and notes to snapshots |

## ⚙️ Requirements

- **Fiji/ImageJ**: Latest version recommended
- **Java**: Version 8 or later
- **Memory**: Minimal (~10MB)
- **OS**: Windows, macOS, or Linux

## 🔨 Building from Source

```bash
# Clone the repository
git clone https://github.com/ttsunglin/DanceNow.git
cd DanceNow

# Build with Maven
mvn clean package

# Find the JAR
ls target/DanceNow.jar
```

### Development Setup
- **IDE**: IntelliJ IDEA or Eclipse with Maven support
- **JDK**: OpenJDK 8+ or Oracle JDK 8+
- **Maven**: Version 3.6+

## File Formats

### CSV Format (with Notes)
```csv
X,Y,Z,T,Note
512,384,1,1,Cell nucleus
1024,768,5,1,Region of interest
256,256,10,3,Background sample
```

### TXT Format (Position only)
```
512,384,1,1
1024,768,5,1
256,256,10,3
```

### Import Flexibility
The plugin intelligently handles various formats:
- **Missing X,Y**: Position skipped with warning
- **Missing Z,T**: Defaults to 1 with notification
- **Out-of-bounds X,Y**: Imported but warns during navigation
- **Out-of-bounds Z,T**: Auto-adjusted to valid range
- **Multiple delimiters**: Comma, space, tab, or mixed

### Excel/Spreadsheet Integration
1. Arrange data in columns (X, Y, Z, T, optional Note)
2. Copy cells from spreadsheet
3. Right-click in DanceNow position list
4. Select "Paste Positions" from context menu
5. Positions automatically parse and validate

## 🎮 Keyboard Shortcuts

| Action | Shortcut | Notes |
|--------|----------|-------|
| Navigate | Mouse click on "Go" | Keyboard shortcuts disabled |
| Add Position | Mouse click on "Add" | Preserves note field |
| Remove Position | Mouse click on "Remove" | Removes selected |
| Context Menu | Right-click on table | Copy/Cut/Paste options |

## 🐛 Troubleshooting

**Issue**: Plugin not appearing in menu
- **Solution**: Ensure JAR is in `plugins/EveryBody/` folder and restart Fiji

**Issue**: Crosshair not visible
- **Solution**: Check "Show center +" checkbox is enabled

**Issue**: Out of bounds error
- **Solution**: Edit position directly in table or remove invalid entry

**Issue**: Can't paste positions
- **Solution**: Use right-click context menu, not keyboard shortcuts

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📧 Contact

For bugs and feature requests, please [open an issue](https://github.com/ttsunglin/DanceNow/issues).

## 🙏 Acknowledgments

- Fiji/ImageJ community for the excellent plugin framework
- All contributors and users who provided feedback

---

<p align="center">Made with ❤️ for the microscopy community</p>

