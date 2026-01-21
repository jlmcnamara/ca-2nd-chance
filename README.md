# CA 2nd Chance Tracker

A Progressive Web App (PWA) for tracking California Lottery 2nd Chance codes on Android devices.

## Features

### Core Functionality
- **Barcode Scanner**: Use your camera to scan ticket barcodes and extract 2nd Chance codes
- **Manual Entry**: Type codes directly with auto-formatting
- **Code Management**: Track pending, entered, and expired codes
- **Status Tracking**: Mark codes as entered after submitting to calottery.com
- **Duplicate Detection**: Prevents entering the same code twice

### Tracking & Limits
- **Monthly Counter**: Tracks your 500 codes/month limit with visual progress bar
- **Expiration Tracking**: Calculates 180-day expiration from game end date
- **Expiration Alerts**: Visual warnings when codes are expiring soon
- **Deadline Display**: Shows countdown to Saturday 11:59 PM entry deadline

### Organization
- **Filter Tabs**: View All, Pending, Entered, or Expired codes
- **Code Types**: Categorize as Scratchers, SuperLotto Plus, or Fantasy 5
- **Quick Copy**: One-tap copy codes to paste into calottery.com
- **Quick Links**: Direct links to CA Lottery 2nd Chance portal and winners page

### History & Stats
- **Monthly History Chart**: Visual bar chart of codes entered over 6 months
- **All-Time Stats**: Total codes, average per month
- **By-Type Breakdown**: See totals for each ticket type

### Data Management
- **CSV Export**: Download all codes as a CSV file
- **CSV Import**: Import codes from a CSV file
- **Local Storage**: All data stored locally on your device
- **Clear Data**: Option to wipe all data

### PWA Features
- **Installable**: Add to home screen for native app experience
- **Offline Support**: Works without internet connection
- **Service Worker**: Caches app for fast loading

## Installation

### Option 1: Local Testing
1. Copy all files to a web server or use a local server
2. Open in Chrome/Edge on Android
3. Tap "Add to Home Screen" when prompted

### Option 2: Deploy to Vercel (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
cd ca-lottery-2nd-chance
vercel
```

### Option 3: GitHub Pages
1. Create a new repository
2. Push all files to the repo
3. Enable GitHub Pages in repository settings
4. Access at `https://yourusername.github.io/repo-name`

### Option 4: Netlify
1. Drag and drop the folder to Netlify
2. Get your URL instantly

## Usage Workflow

1. **Buy lottery tickets** (Scratchers, SuperLotto Plus, Fantasy 5)
2. **Open the app** and tap "Scan Ticket" or "Manual Entry"
3. **Scan/enter the 2nd Chance code** from your ticket
4. **Select ticket type** and optionally enter game end date
5. **Codes are saved** with calculated expiration dates
6. **When ready to enter**, tap "Enter Codes" quick link
7. **Copy codes** one by one and paste into calottery.com
8. **Mark as entered** in the app after submitting
9. **Check winners** weekly using the quick link

## Technical Details

### Files
- `index.html` - Main application (single-page app)
- `manifest.json` - PWA manifest for installation
- `sw.js` - Service worker for offline caching
- `icon-192.svg` - App icon

### Dependencies
- ZXing library (loaded from CDN) - Barcode scanning
- Google Fonts - Typography

### Browser Support
- Chrome/Edge on Android (full support)
- Safari on iOS (limited PWA features)
- Desktop browsers (testing only)

### Data Storage
All data is stored in browser localStorage:
- `ca2ndchance_codes` - Array of code objects
- `ca2ndchance_settings` - User preferences
- `ca2ndchance_history` - Monthly code counts

## Code Object Structure
```json
{
  "id": "unique-id",
  "code": "ABC123XYZ",
  "type": "scratchers|superlotto|fantasy5",
  "status": "pending|entered|expired",
  "addedAt": "2025-01-19T12:00:00.000Z",
  "baseDate": "2025-01-15T00:00:00.000Z",
  "expiresAt": "2025-07-14T00:00:00.000Z",
  "enteredAt": null
}
```

## CA Lottery 2nd Chance Rules
- Submit up to 500 codes per month
- Entry deadline: Saturday at 11:59 PM Pacific
- Scratchers codes expire 180 days after game end date
- SuperLotto Plus and Fantasy 5 codes expire 180 days from purchase
- Must be 18+ with valid California address
- Codes must be submitted from within California

## License
MIT - Use freely for personal lottery tracking.

## Disclaimer
This app is not affiliated with or endorsed by the California State Lottery. It's a personal tracking tool to help manage your 2nd Chance entries. Always refer to calottery.com for official rules and entry submission.
