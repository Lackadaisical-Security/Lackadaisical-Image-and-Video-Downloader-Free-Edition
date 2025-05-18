# Lackadaisical Image Downloader - Server Instructions

This document provides instructions on how to start and stop the Lackadaisical Image Downloader server using the provided scripts.

## Requirements

- Windows operating system
- Node.js (version 16.0.0 or higher)
- Port 3000 available on your system

## Starting the Server

You have two options to start the server:

### Option 1: Using Batch Script (Simple)

1. Double-click on `start-server.bat` in Windows Explorer
2. The server will start in a command prompt window
3. Your default web browser will open to http://localhost:3000
4. The server will continue running in the background

### Option 2: Using PowerShell Script (Recommended)

1. Right-click on `start-server.ps1` and select "Run with PowerShell"
   - If you get a security warning, you might need to run: `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Bypass`
2. The script will:
   - Check if Node.js is installed
   - Create a `.env` file if it doesn't exist
   - Check if port 3000 is already in use
   - Start the server in a new PowerShell window
   - Open your browser to http://localhost:3000

## Configuration (.env File)

The application uses a `.env` file for configuration. This file will be created automatically when you run the start scripts if it doesn't exist. You can manually edit this file to customize the application settings:

```
# Server port
PORT=3000

# Environment (development or production)
NODE_ENV=production

# Maximum file size for download in bytes (100MB)
MAX_FILE_SIZE=104857600

# Download timeout in milliseconds (30 seconds)
DOWNLOAD_TIMEOUT=30000

# CORS settings (use * for development, specific domains for production)
CORS_ORIGIN=*

# Downloads directory (relative to project root)
DOWNLOADS_DIR=downloads
```

## Stopping the Server

You have two options to stop the server:

### Option 1: Using Batch Script (Simple)

1. Double-click on `stop-server.bat` in Windows Explorer
2. The script will find and terminate the Node.js process running on port 3000

### Option 2: Using PowerShell Script (Recommended)

1. Right-click on `stop-server.ps1` and select "Run with PowerShell"
2. The script will:
   - Find processes listening on port 3000
   - Identify if they are Node.js processes
   - Safely terminate the server
   - Provide options for handling unexpected situations

### Manual Stopping

If the scripts don't work, you can also stop the server manually:

1. Press Ctrl+C in the command window where the server is running, or
2. Close the command window, or
3. Open Task Manager (Ctrl+Shift+Esc), find the Node.js process, and end it

## Troubleshooting

### Server Won't Start

- Make sure Node.js is installed and in your PATH
- Check if another application is already using port 3000
- Try running the server manually with `node server.js`

### Server Won't Stop

- Try the PowerShell method, which has better error handling
- Use Task Manager to identify and kill Node.js processes
- Restart your computer if all else fails

## Customizing Port

If you need to use a different port:

1. Edit the `.env` file and change the PORT value
2. Edit the port number in both start and stop scripts (search for "3000" and replace with your preferred port)

## Running as a Service

For permanent installation as a Windows service, use the included `install-service.js` script:

```
npm install -g node-windows
npm link node-windows
node install-service.js
```

After installation, the service will start automatically on system boot. 