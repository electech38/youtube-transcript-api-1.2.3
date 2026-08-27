# 🎥 YouTube Scraper Pro

Professional YouTube video data extraction tool with beautiful GUI.

## ✨ Features

### Core Functionality
- ✅ Extract video metadata (URL, Title, Thumbnail, Views, Date)
- ✅ Download complete video transcripts
- ✅ Support for multiple videos/channels
- ✅ Real-time progress tracking
- ✅ Export to CSV or Google Sheets
- ✅ Import URLs from CSV files

### User Interface
- 🎨 Modern, dark-themed GUI using CustomTkinter
- 📊 Real-time progress bars
- 🔄 Multi-threaded processing
- 💾 Customizable save locations
- 📁 Drag & drop support (coming soon)

### Versions
- **DEMO**: 5-day trial period, full features
- **FULL**: Unlimited usage, no restrictions

---

## 📦 Installation

### Prerequisites
- Python 3.8 or higher
- YouTube Data API v3 key (free from Google Cloud Console)
- Google Cloud credentials for Sheets export (optional)

### Step 1: Clone Repository
```bash
git clone <repository-url>
cd youtube-scraper
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Get YouTube API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create a new project
3. Enable **YouTube Data API v3**
4. Create credentials → API Key
5. Copy the API key

### Step 4 (Optional): Setup Google Sheets

1. In Google Cloud Console, enable **Google Sheets API**
2. Create credentials → OAuth 2.0 Client ID
3. Download `credentials.json`
4. Place in `config/credentials.json`

---

## 🚀 Usage

### Running from Source

**Demo Version (5-day trial):**
```bash
python main_demo.py
```

**Full Version:**
```bash
python main_full.py
```

### Using the GUI

1. **Enter API Key**
   - Paste your YouTube API key in the top field

2. **Add Video URLs**
   - Paste YouTube URLs (one per line)
   - Or click "Import CSV" to load from file
   - Supports:
     - Individual video URLs
     - Channel URLs (scrapes all videos)
     - Playlists (coming soon)

3. **Choose Export Format**
   - CSV: Local file saved to Documents
   - Google Sheets: Creates new spreadsheet
   - Both: Exports to both formats

4. **Start Scraping**
   - Click "🚀 Start Scraping"
   - Watch real-time progress
   - Results saved automatically

### CSV Import Format

Your CSV file should have URLs in any of these column names:
- `url`
- `URL`
- `link`
- `YouTube Video Link`

Example:
```csv
url
https://www.youtube.com/watch?v=dQw4w9WgXcQ
https://www.youtube.com/watch?v=9bZkp7q19f0
```

---

## 🏗️ Building Executables

### Build DEMO Version
```bash
pyinstaller build_demo.spec
```

Output: `dist/YouTube_Scraper_DEMO.exe`

### Build FULL Version
```bash
pyinstaller build_full.spec
```

Output: `dist/YouTube_Scraper_PRO.exe`

### Build Notes
- First build may take 5-10 minutes
- EXE size: ~40-60 MB
- Runs on Windows 10/11 without Python installed
- Antivirus may flag (false positive) - add exclusion if needed

---

## 📂 Project Structure

```
youtube-scraper/
├── src/
│   ├── scraper/
│   │   └── youtube_scraper.py    # Core scraping logic
│   ├── export/
│   │   ├── csv_exporter.py       # CSV export
│   │   └── sheets_exporter.py    # Google Sheets export
│   ├── gui/
│   │   └── main_window.py        # CustomTkinter GUI
│   └── utils/
│       ├── config.py              # Configuration
│       └── license.py             # Trial/license system
├── config/                        # Config files
├── assets/                        # Images/icons
├── main_demo.py                   # Demo entry point
├── main_full.py                   # Full entry point
├── build_demo.spec               # PyInstaller config (demo)
├── build_full.spec               # PyInstaller config (full)
├── requirements.txt              # Python dependencies
└── README.md                     # This file
```

---

## 🔧 Configuration

### Default Settings

Edit `src/utils/config.py`:

```python
# Trial period for demo version
TRIAL_DAYS = 5

# Default output directory
DEFAULT_OUTPUT_DIR = "~/Documents/YouTube_Scraper_Output"

# GUI theme
THEME = "blue"  # blue, green, dark-blue
```

### API Rate Limits

YouTube API free quota: **10,000 requests/day**

Cost per operation:
- Search: 100 units
- Video details: 1 unit
- Typical scraping: 1-3 units per video

**Estimate**: Can scrape ~3,000-5,000 videos/day with free quota

---

## 📊 Export Format

### CSV Output
```csv
YouTube Video Link,Thumbnail,Title,Views Count,Transcript
https://youtube.com/...,https://i.ytimg.com/...,Video Title,1234567,Full transcript text...
```

### Google Sheets Output
Same format as CSV, with:
- **Bold headers**
- **Blue header background**
- **Auto-resized columns**
- **Shareable link** (view-only)

---

## ⚠️ Limitations & Notes

### Demo Version
- ✅ Full features enabled
- ⏰ 5-day trial from first run
- 🔒 Trial cannot be reset (uses system date)

### API Limitations
- YouTube API required (free tier sufficient)
- Transcript not available for all videos
- Some videos may be age-restricted or region-locked

### Performance
- Processing speed: ~2-5 seconds per video
- Limited by YouTube API rate limits
- Google Sheets: Max 10 million cells per spreadsheet

---

## 🐛 Troubleshooting

### "API Key Invalid"
- Verify key is correct
- Check API is enabled in Cloud Console
- Ensure billing is enabled (free tier works)

### "Transcript Not Available"
- Video may not have captions
- Try manual captions vs auto-generated
- Check video privacy settings

### "Google Sheets Authentication Failed"
- Download fresh `credentials.json`
- Delete `config/token.json` and re-authenticate
- Check Sheets API is enabled

### EXE Won't Run
- Windows Defender may block (add exclusion)
- Try running as administrator
- Check antivirus logs

---

## 📝 License

**Demo Version**: 5-day trial, full features
**Full Version**: Single-user license

For commercial use or multi-user licenses, contact the developer.

---

## 🤝 Support

For issues or feature requests:
1. Check this README
2. Review error messages
3. Check API quotas
4. Contact developer with:
   - Error screenshot
   - Steps to reproduce
   - System info (Windows version, Python version)

---

## 🎯 Roadmap

- [ ] Playlist support
- [ ] Subtitle language selection
- [ ] Video download option
- [ ] Batch channel processing
- [ ] Custom data filters
- [ ] Export templates
- [ ] Automatic scheduling
- [ ] API quota monitoring

---

## 👨‍💻 Developer

Built with ❤️ using:
- Python 3.10+
- CustomTkinter
- YouTube Data API v3
- Google Sheets API
- PyInstaller

---

## 📄 Changelog

### Version 1.0.0 (2025-01-11)
- Initial release
- Core scraping features
- CSV and Google Sheets export
- Trial system for demo version
- Modern GUI with CustomTkinter
