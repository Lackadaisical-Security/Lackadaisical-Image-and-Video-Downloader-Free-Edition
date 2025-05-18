# Lackadaisical Image Downloader - Free Edition

A free tool for downloading images from the web with support for proxies, authentication, and basic image processing.

## Features

- Download images and videos from various sources
- Optional proxy support for anonymous downloading
- Authentication support for protected content
- Image processing capabilities (format conversion, metadata stripping)
- Simple and user-friendly interface

## Requirements

- Node.js 16.0 or higher
- NPM or Yarn package manager
- Windows, macOS, or Linux operating system

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/username/lackadaisical-image-downloader.git
   cd lackadaisical-image-downloader
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Create a `.env` file in the root directory (optional):
   ```
   PORT=3000
   NODE_ENV=development
   MAX_FILE_SIZE=104857600
   DOWNLOAD_TIMEOUT=30000
   CORS_ORIGIN=*
   ```

## Running the Application

### Development Mode

```
npm run dev
```

This will start the server with hot reloading using nodemon.

### Production Mode

```
NODE_ENV=production npm start
```

For Windows Command Prompt:
```
set NODE_ENV=production&& npm start
```

For Windows PowerShell:
```
$env:NODE_ENV="production"; npm start
```

## Deployment Options

### Hosting on Windows Server

1. Install Node.js on your Windows Server
2. Set up the application as a Windows Service using a tool like `node-windows`:
   ```
   npm install -g node-windows
   npm link node-windows
   ```
3. Create a service installer script (e.g., `install-service.js`):
   ```javascript
   const Service = require('node-windows').Service;
   const path = require('path');

   const svc = new Service({
     name: 'Lackadaisical Image Downloader',
     description: 'Image downloader service',
     script: path.join(__dirname, 'server.js'),
     env: [
       { name: 'NODE_ENV', value: 'production' },
       { name: 'PORT', value: 3000 }
     ]
   });

   svc.on('install', function() {
     svc.start();
     console.log('Service installed and started successfully');
   });

   svc.install();
   ```
4. Run the installer:
   ```
   node install-service.js
   
## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| PORT | Port the server will listen on | 3000 |
| NODE_ENV | Environment mode (development/production) | development |
| MAX_FILE_SIZE | Maximum file size in bytes | 104857600 (100MB) |
| DOWNLOAD_TIMEOUT | Download timeout in milliseconds | 30000 (30s) |
| CORS_ORIGIN | CORS settings | * |

## Security Considerations

- By default, the app includes security headers like CSP, HSTS, and XSS protection
- For production use, consider setting up HTTPS
- Regularly update dependencies to patch security vulnerabilities
- Be cautious with proxy settings in production environments

## Troubleshooting

- If downloads fail with timeout errors, increase the `DOWNLOAD_TIMEOUT` value
- If you cannot download large files, increase the `MAX_FILE_SIZE` value
- Check the server logs for detailed error messages

## About

Lackadaisical Image Downloader is developed by Lackadaisical Security, providing simple 
and effective image downloading solutions.

## Contact

- Website: https://lackadaisical-security.com
- Support: support@lackadaisical-security.com

## License

This project is licensed under the Lackadaisical Restricted Use License - see the [LICENSE.md](LICENSE.md) file for details.
This license allows personal use and modification only. Distribution, selling, or sublicensing is prohibited without permission from Lackadaisical Security.
Any modifications must maintain the original attribution and license.