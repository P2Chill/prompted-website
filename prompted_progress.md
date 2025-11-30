# Prompted.sbs - Progress

## 2025-11-30 - Favicon Restoration

### Robot Head Favicon Restored
- Restored original robot head favicon (without antenna, fills full space)
- User preference: favicon and logo don't need to match
- Logo provides detail for large display, favicon optimized for small size (16x16px)
- Backup of logo favicon saved as `favicon_logo_backup.ico`

**Git history:**
```
e5f3564 - Update favicon with Gemini-generated brain logo (previous)
99e4168 - Switch to ICO format favicon like qBittorrent (robot head - now active)
```

**Files:**
- `favicon.ico` - Robot head (active)
- `favicon_logo_backup.ico` - Brain logo backup
- `logo.png` - Brain logo for website header (unchanged)

## Previous Work

### 2025-11-30 - Logo Implementation
- Added Gemini-generated brain logo to website header
- Created high-resolution logo.png
- Initially updated favicon to match logo
- User decided to revert favicon to robot head for better small-size clarity

### 2025-11-28 - Mobile Improvements
- Enhanced mobile responsiveness
- Documented improvements in MOBILE_IMPROVEMENTS.md

### Initial Setup
- Multi-language portfolio site (NL/EN/FR)
- Cloudflare Tunnel deployment on NAS
- Robot head favicon design (no antenna, space-filling)
