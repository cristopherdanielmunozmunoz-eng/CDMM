# 🌐 IP Address Tracker

A comprehensive web application to monitor and track IP addresses of users who access your page. Choose between a simple browser-based solution or a full-featured backend with database persistence.

## Features

### Core Functionality
- ✅ Real-time IP address capture
- ✅ Geolocation data (city, country, coordinates)
- ✅ Access timestamp logging
- ✅ User agent detection (browser info)
- ✅ Referrer tracking
- ✅ ISP information (backend only)
- ✅ Auto-refresh capability
- ✅ CSV export functionality

### Statistics
- 📊 Total visits
- 🔍 Unique IP addresses
- 📅 Today's visit count
- 🏆 Top countries
- 🏙️ Top cities
- 🌐 Top ISPs (backend only)

## Quick Start

### Option 1: Browser-Only (No Setup Required)

1. Open `index.html` in your web browser
2. Your IP will be captured automatically
3. Data is stored in browser's local storage
4. No server required

**Pros:**
- Zero configuration
- No dependencies
- Works offline (after first load)
- Privacy-focused (local storage only)

**Cons:**
- Data persists only in that browser
- Smaller storage capacity
- No persistent database

### Option 2: Full Backend (Recommended for Production)

#### Prerequisites
- Node.js 14+ and npm

#### Installation

1. Navigate to the `ip-tracker` directory:
   ```bash
   cd ip-tracker
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the server:
   ```bash
   npm start
   ```
   - Development: `npm run dev` (with auto-reload)
   - Production: `npm start`

4. Open your browser and navigate to:
   ```
   http://localhost:3000
   ```

**Pros:**
- Persistent SQLite database
- Scalable
- Advanced statistics
- API endpoints for integration
- Better data management

**Cons:**
- Requires Node.js
- More resource usage

## API Endpoints

### Record Access
```
POST /api/record-access
```
Records a new visitor access (called automatically on page load)

### Get All Logs
```
GET /api/logs
```
Returns all access logs with full details

**Response:**
```json
[
  {
    "id": 1,
    "ip_address": "192.168.1.1",
    "timestamp": "2024-05-10T12:34:56Z",
    "country": "United States",
    "city": "New York",
    "latitude": 40.7128,
    "longitude": -74.0060,
    "isp": "Example ISP",
    "user_agent": "Mozilla/5.0...",
    "referrer": "google.com"
  }
]
```

### Get Statistics
```
GET /api/statistics
```
Returns aggregated statistics

**Response:**
```json
{
  "totalVisits": 150,
  "uniqueIPs": 45,
  "todayVisits": 23,
  "topCountries": [...],
  "topCities": [...],
  "topISPs": [...]
}
```

### Get Logs by Date Range
```
GET /api/logs/range/:startDate/:endDate
```
Example: `/api/logs/range/2024-05-01/2024-05-10`

### Get Logs for Specific IP
```
GET /api/logs/ip/:ipAddress
```
Example: `/api/logs/ip/192.168.1.1`

### Export as CSV
```
GET /api/export/csv
```
Downloads all logs as CSV file

### Delete All Logs
```
DELETE /api/logs
```
Removes all recorded access logs

## Directory Structure

```
ip-tracker/
├── index.html          # Main HTML page
├── styles.css          # Styling
├── script.js           # Frontend logic
├── server.js           # Express backend
├── package.json        # Dependencies
├── logs.db             # SQLite database (created on first run)
└── README.md           # This file
```

## Data Collected

| Field | Description |
|-------|-------------|
| IP Address | User's public IP |
| Timestamp | Date and time of access |
| Country | User's country |
| City | User's city |
| Latitude/Longitude | Geographic coordinates |
| ISP | Internet Service Provider |
| User Agent | Browser and OS information |
| Referrer | Source of the visit |

## Browser Support

- ✅ Chrome/Edge (Latest)
- ✅ Firefox (Latest)
- ✅ Safari (Latest)
- ✅ Mobile browsers
- ✅ Responsive design

## Configuration

### Port Configuration
Set custom port using environment variable:
```bash
PORT=8080 npm start
```

### Database Location
SQLite database file is created at `./logs.db` by default

## Privacy & Security

⚠️ **Important Considerations:**
- Users should be notified that their IP is being tracked
- Follow GDPR, CCPA, and local privacy laws
- Consider anonymizing IP data
- Implement proper data retention policies
- Use HTTPS in production
- Secure API endpoints appropriately

## Geolocation APIs Used

- **Frontend:** ipify (free tier)
- **Backend:** ipapi.co (free tier)

Both services provide free IP geolocation data with usage limits.

## Troubleshooting

### IP Shows as "Unable to fetch"
- Check internet connection
- Geolocation API might be rate-limited
- Try refreshing the page

### Database errors (Backend)
- Ensure SQLite3 is installed
- Check file permissions on logs.db
- Delete logs.db and restart server

### CORS errors
- CORS is enabled by default
- Modify `server.js` if needed for specific origins

## Performance Tips

### For Large Scale Deployment
- Use a production-grade database (PostgreSQL, MySQL)
- Implement caching
- Use reverse proxy (Nginx)
- Enable compression
- Implement request throttling
- Consider data archival for old logs

## License

MIT License - Feel free to use and modify

## Support

For issues or questions, refer to the [GitHub Repository](https://github.com/cristopherdanielmunozmunoz-eng/CDMM)

---

**Created with ❤️** - IP Address Tracker v1.0.0
