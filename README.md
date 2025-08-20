# Stremio Library Exporter

> Automated Python toolkit using Playwright to extract your Stremio library and export movies to CSV format. Perfect for importing your movie collection into platforms like [Letterboxd](https://letterboxd.com).

## Features

- **Fully Automated**: No manual clicking or scrolling required
- **Secure Authentication**: Uses `.env` file for credential management
- **Multi-Browser Support**: Works with Chrome, Firefox, and Safari via Playwright
- **Smart Categorization**: Automatically separates watched movies from watchlist
- **API-Powered**: Uses official Stremio API for reliable data extraction
- **Organized Output**: Clean CSV files ready for import to other platforms

## Prerequisites

1. Python 3.12+
2. [uv](https://docs.astral.sh/uv/getting-started/installation/) Package manager


## Setup and Usage

1. **Clone this repository**

    ```bash
    git clone https://github.com/SourasishBasu/stremio-library-exporter.git
    ```
2. **Configure your credentials**:
   Create an `.env` file in project root and replace the placeholder values:
   ```env
   STREMIO_EMAIL=your_stremio_email@example.com
   STREMIO_PASSWORD=your_actual_password
   ```

3. **Run the main extractor**:
   ```bash
   uv sync
   uv run playwright install
   uv run movie_extractor.py
   ```

 
## How It Works

The extraction process follows these automated steps:
1. 🌐 **Login**: Opens web.stremio.com and authenticates using your credentials
2. 🔑 **Auth Extraction**: Retrieves your session `authKey` from localStorage
3. 📨 **API Request**: Makes authenticated requests to `api.strem.io/api/datastoreMeta`
4. 📊 **Data Processing**: Parses movie data and categorizes by watch status
5. 💾 **CSV Export**: Saves organized data to timestamped CSV files in `output/` folder
6. 📤 **Import Ready**: Use generated CSVs with [Letterboxd Import](https://letterboxd.com/import/)

### File Structure

```
stremio-library-exporter/
├── output/                # Generated CSV files
│   ├── watched_api_*.csv
│   └── watchlist_api_*.csv
├── movie_extractor.py
├── auth_extractor.py      
├── .env                  
├── .env.example      
├── pyproject.toml
└── README.md 
```

## Troubleshooting

### Authentication Issues
- **Verify credentials**: Double-check `.env` file format and values
- **Check logs**: Review console output for detailed error messages
- **Test manually**: Try logging into web.stremio.com manually first

### Browser Issues
- **Try different browsers**: Use `--browser firefox` or `--browser webkit`
- **Visible mode**: Set `headless=False` in scripts to watch the automation
- **Update browsers**: Run `uv run playwright install` to update browser binaries
- **Check dependencies**: Ensure all packages are installed with `uv sync`

---