# EM Researchers Citation Tracker - Mass General Brigham

This tool tracks citation statistics for Emergency Medicine researchers at Mass General Brigham by scraping data from their Google Scholar profiles.

## Overview

The project displays researcher profiles in an interactive table showing:
- **Name & Affiliation**: Links to Google Scholar profiles
- **Year**: First citation year
- **Citations**: Total citation count and average citations per year
- **h-index**: Research productivity measure and average per year
- **i10-index**: Number of publications with 10+ citations and average per year

## Setup

### Prerequisites
- [Node.js](http://nodejs.org/) installed on your machine

### Installation

1. Clone the repository:
```bash
git clone https://github.com/JoshGMGB/em-researchers-mgb.git
cd em-researchers-mgb
```

2. Install dependencies:
```bash
npm install
```

## Adding Researchers

Edit `people-mgb.json` and add researchers with their Google Scholar profile URLs:

```json
{
  "John Smith, MD": "https://scholar.google.com/citations?user=ABC123&hl=en",
  "Jane Doe, MD": "https://scholar.google.com/citations?user=XYZ789&hl=en"
}
```

To find a Google Scholar profile URL:
1. Go to [Google Scholar](https://scholar.google.com/)
2. Search for the researcher
3. Click on their profile
4. Copy the URL from the address bar

## Running the Scraper

```bash
npm run scrape
```

This will:
1. Fetch data from each researcher's Google Scholar profile
2. Extract citation statistics
3. Generate `stats-mgb.js` with the compiled data
4. Output the current timestamp

**Note:** The scraper includes a 1-second delay between requests to be respectful of Google's servers.

## Viewing the Results

Open `index.html` in your browser to see the interactive table with:
- Sortable columns (click headers)
- Search/filter functionality
- Automatic ranking

## Keeping Data Updated

### Manual Updates
Re-run the scraper periodically:
```bash
npm run scrape
git add stats-mgb.js
git commit -m "Update researcher data"
git push
```

### Automated Updates (GitHub Actions)
A GitHub Actions workflow is included (`.github/workflows/scrape.yml`) that automatically runs the scraper weekly on Sunday at midnight UTC.

You can also manually trigger it from the Actions tab in your repository.

## Hosting on GitHub Pages

1. Go to repository Settings → Pages
2. Set "Source" to "Deploy from a branch"
3. Select the branch containing your code (typically `main` or `master`)
4. Your site will be available at: `https://JoshGMGB.github.io/em-researchers-mgb/`

## Technologies Used

- **scrape.js**: Node.js web scraper using:
  - `request` - HTTP requests
  - `cheerio` - HTML parsing
  - `async` - Asynchronous control flow
- **index.html**: Interactive table display using:
  - jQuery
  - [TableSorter](http://tablesorter.com/) - Table sorting and filtering

## Limitations

- **Google Scholar profiles required**: Researchers must have public Google Scholar profiles
- **Manual list maintenance**: You must manually add/remove researchers from `people-mgb.json`
- **Rate limiting**: The scraper includes delays to respect server load
- **Data accuracy**: Google Scholar data may contain errors or duplicates

## Troubleshooting

### Scraper hangs or fails
- Check your internet connection
- Verify Google Scholar profile URLs are correct
- Google may temporarily block requests if too many are made too quickly

### Data not updating
- Confirm `stats-mgb.js` was generated correctly
- Clear browser cache (Ctrl+Shift+Delete or Cmd+Shift+Delete)
- Refresh the page

### Profile data missing
- The researcher's Google Scholar profile may be private
- Profile URL may be incorrect
- Google Scholar may be blocking requests

## Credits

Based on the work of:
- Allison McCoy (Vanderbilt University Medical Center)
- Jimmy Lin (University of Waterloo)
- Adam Landman (Citation Scraper EM project)

## License

MIT License

## Questions or Issues?

Feel free to open an issue on GitHub or contact the maintainer.
