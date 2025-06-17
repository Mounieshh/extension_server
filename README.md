# Productivity Tracker Chrome Extension

A Chrome extension that helps you track and manage your website usage to improve productivity.

## Features

- Track time spent on websites
- Block distracting websites
- View daily and weekly productivity reports
- Sync data across devices using a unique device ID

## Project Structure

```
.
├── backend/                 # Node.js + Express backend
│   ├── src/
│   │   ├── config/         # Database configuration
│   │   ├── controllers/    # Route controllers
│   │   ├── models/         # Mongoose models
│   │   ├── routes/         # API routes
│   │   └── app.js          # Main application file
│   └── package.json
│
└── frontend/               # Chrome extension frontend
    ├── public/            # Static files
    │   ├── manifest.json  # Extension manifest
    │   ├── background.js  # Background script
    │   ├── content.js     # Content script
    │   ├── popup.html     # Popup page
    │   └── blocked.html   # Blocked site page
    ├── src/              # React components
    │   ├── components/   # React components
    │   └── main.jsx      # React entry point
    └── package.json
```

## Setup Instructions

### Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the backend directory with the following content:
   ```
   PORT=5000
   MONGO_URI=mongodb://localhost:27017/productivity-tracker
   ```

4. Start the backend server:
   ```bash
   npm run server
   ```

### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Build the extension:
   ```bash
   npm run build
   ```

4. Load the extension in Chrome:
   - Open Chrome and go to `chrome://extensions/`
   - Enable "Developer mode"
   - Click "Load unpacked"
   - Select the `frontend/dist` directory

## API Endpoints

### Website Usage

- `POST /api/website-usage`
  - Save website usage data
  - Body: `{ deviceId, url, title, timeSpent }`

- `GET /api/website-usage`
  - Get website usage data
  - Query params: `deviceId, startDate, endDate`

- `GET /api/website-usage/report`
  - Get productivity report
  - Query params: `deviceId, period` (daily/weekly)

### Blocked Sites

- `POST /api/blocked-sites`
  - Add new blocked site
  - Body: `{ deviceId, url, reason }`

- `GET /api/blocked-sites`
  - Get all blocked sites
  - Query params: `deviceId`

- `PUT /api/blocked-sites/:id`
  - Update blocked site
  - Query params: `deviceId`
  - Body: `{ url, reason, isActive }`

- `DELETE /api/blocked-sites/:id`
  - Delete blocked site
  - Query params: `deviceId`

## Development

- Backend development server: `npm run server`
- Frontend development: `npm run dev`

## Building for Production

- Backend: `npm run start`
- Frontend: `npm run build`

## License

ISC 