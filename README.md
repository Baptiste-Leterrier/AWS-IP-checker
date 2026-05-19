# AWS IP Range Checker

[![AWS IP Checker](https://img.shields.io/badge/AWS-IP%20Checker-orange)](https://github.com/Baptiste-Leterrier/AWS-IP-checker)

A real-time web application to identify AWS services and regions for any IP address. Check if an IP belongs to AWS infrastructure and get detailed information about the associated service, region, and CIDR block.

## 🌟 Features

- **Real-time IP Lookup** - Instantly check if an IP address belongs to AWS
- **IPv4 & IPv6 Support** - Works with both IPv4 and IPv6 addresses
- **Live Data** - AWS IP ranges are fetched automatically from the official AWS data source
- **Detailed Results** - Get service name, region, CIDR block, and network border group information
- **Precise Matching** - Automatically prioritizes the most specific CIDR match
- **Responsive Design** - Works seamlessly on desktop, tablet, and mobile devices
- **No Installation** - Runs entirely in the browser
- **Error Handling** - Automatic CORS proxy fallback for reliable data fetching

## 🚀 Getting Started

### Quick Start

Simply open the `index.html` file in your web browser:

```bash
git clone https://github.com/Baptiste-Leterrier/AWS-IP-checker.git
cd AWS-IP-checker
open index.html  # macOS
# or
xdg-open index.html  # Linux
# or
start index.html  # Windows
```

Or use it online by cloning this repo and serving the file via any web server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx http-server

# Using Live Server (VS Code extension)
```

Then navigate to `http://localhost:8000` (or your configured port).

## 📖 How to Use

1. **Enter an IP Address**: Type an IPv4 (e.g., `3.4.12.4`) or IPv6 address in the search box
2. **Search**: Click the "Search" button or press Enter
3. **View Results**: See the AWS service, region, and CIDR block information

### Example Searches

- `3.4.12.4` (IPv4)
- `2600:1f13:b40:c200:0:0:0:0` (IPv6)

## 🛠️ Technical Details

### Architecture

- **Frontend**: HTML5, Tailwind CSS, Lucide Icons
- **Data Source**: [AWS IP Ranges JSON](https://ip-ranges.amazonaws.com/ip-ranges.json)
- **CORS Handling**: Dual-fetch strategy with proxy fallback
- **IP Matching**: CIDR binary comparison for both IPv4 and IPv6

### Key Components

#### IPv4 CIDR Matching (`isIp4InCidr`)
Converts IP addresses and CIDR ranges to binary and compares the specified number of bits.

#### IPv6 CIDR Matching (`isIp6InCidr`)
Handles IPv6 address expansion (including compressed notation with `::`) and CIDR comparison.

#### Data Fetching (`fetchAwsData`)
- Attempts direct fetch from AWS data source
- Falls back to CORS proxy (`allorigins.win`) if direct access is blocked
- Stores IPv4 prefixes and IPv6 prefixes with metadata

### Browser Support

Works on all modern browsers supporting:
- ES6 JavaScript
- Fetch API
- CSS Grid & Flexbox

## 📊 Data Structure

The application tracks:
- **IPv4 Prefixes**: CIDR blocks, service, region, network border group
- **IPv6 Prefixes**: IPv6 CIDR blocks, service, region, network border group
- **Sync Token**: Unique identifier for the data version
- **Creation Date**: When the data was last updated

## ⚙️ How It Works

1. **On Load**: Application automatically fetches the latest AWS IP ranges
2. **Status Display**: Shows count of IPv4 and IPv6 ranges and last update time
3. **Search**: User enters an IP address
4. **Matching**: App filters ranges containing that IP using binary CIDR comparison
5. **Sorting**: Results sorted by CIDR specificity (highest prefix bits first)
6. **Display**: Shows matched services with all relevant metadata

## 🔄 Data Updates

AWS updates their IP ranges regularly. This application:
- Fetches fresh data every time you load the page
- Caches data in memory during your session
- Uses `createDate` from AWS JSON to show last sync time

To get the latest data, simply refresh the page.

## 🛡️ Privacy & Security

- **Client-Side Only**: All processing happens in your browser
- **No Tracking**: No data is stored or transmitted to third parties
- **Open Source**: Full code visibility for security auditing
- **CORS Proxy**: Uses `allorigins.win` as a fallback for CORS handling

## 📝 License

This project is provided as-is for educational and informational purposes.

## 🤝 Contributing

Found a bug or have a suggestion? Feel free to:
- Open an issue
- Submit a pull request
- Share feedback

## 📚 Resources

- [AWS IP Address Ranges Documentation](https://docs.aws.amazon.com/general/latest/gr/aws-ip-ranges.html)
- [AWS IP Ranges JSON Endpoint](https://ip-ranges.amazonaws.com/ip-ranges.json)
- [CIDR Notation Explained](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

---

**Made with ❤️ by Baptiste-Leterrier**
