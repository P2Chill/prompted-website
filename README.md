# Prompted.sbs - Professional Portfolio Website

A modern, responsive portfolio website showcasing AI integration, infrastructure automation, and technical consulting services.

## Features

- 🎨 Modern, professional design with gradient accents
- 📱 Fully responsive layout (mobile, tablet, desktop)
- ⚡ Fast loading with optimized CSS and vanilla JavaScript
- 🎯 Clear service offerings and technical expertise sections
- 📧 Contact form with email integration
- ✨ Smooth animations and scroll effects
- 🔍 SEO-optimized structure

## Structure

```
prompted-website/
├── index.html      # Main HTML file
├── styles.css      # All styling and responsive design
├── script.js       # Interactive features and animations
└── README.md       # This file
```

## Deployment Options

### Option 1: GitHub Pages (Free)

1. Create a new repository on GitHub (e.g., `prompted-website`)
2. Push the website files:
   ```bash
   cd /tmp/prompted-website
   git init
   git add .
   git commit -m "Initial commit: Professional portfolio website"
   git remote add origin https://github.com/P2Chill/prompted-website.git
   git push -u origin main
   ```
3. Enable GitHub Pages in repository settings
4. Set custom domain `prompted.sbs` in settings
5. Add CNAME record in your domain registrar:
   - Type: CNAME
   - Name: www (or @)
   - Value: p2chill.github.io

### Option 2: Cloudflare Pages (Free, Recommended)

1. Log in to Cloudflare dashboard
2. Go to "Pages" and click "Create a project"
3. Connect your GitHub account
4. Select the repository
5. Deploy settings:
   - Build command: (leave empty - static site)
   - Build output directory: /
6. Add custom domain `prompted.sbs`
7. Cloudflare automatically handles SSL/TLS

### Option 3: Nginx on Your Infrastructure

Deploy to your existing infrastructure:

1. Copy files to web server:
   ```bash
   scp -r /tmp/prompted-website/* user@yourserver:/var/www/prompted
   ```

2. Nginx configuration (`/etc/nginx/sites-available/prompted.sbs`):
   ```nginx
   server {
       listen 80;
       listen [::]:80;
       server_name prompted.sbs www.prompted.sbs;

       root /var/www/prompted;
       index index.html;

       location / {
           try_files $uri $uri/ =404;
       }

       # Security headers
       add_header X-Frame-Options "SAMEORIGIN" always;
       add_header X-Content-Type-Options "nosniff" always;
       add_header X-XSS-Protection "1; mode=block" always;

       # Cache static assets
       location ~* \.(css|js|jpg|jpeg|png|gif|ico|svg)$ {
           expires 1y;
           add_header Cache-Control "public, immutable";
       }
   }
   ```

3. Enable site and reload Nginx:
   ```bash
   sudo ln -s /etc/nginx/sites-available/prompted.sbs /etc/nginx/sites-enabled/
   sudo nginx -t
   sudo systemctl reload nginx
   ```

4. Add SSL with Let's Encrypt:
   ```bash
   sudo certbot --nginx -d prompted.sbs -d www.prompted.sbs
   ```

### Option 4: Cloudflare Tunnel (Your Current Setup)

Use your existing Cloudflare tunnel infrastructure:

1. Create directory on Mini PC:
   ```bash
   mkdir -p ~/docker-data/prompted-website
   cp /tmp/prompted-website/* ~/docker-data/prompted-website/
   ```

2. Add to Nginx Proxy Manager:
   - Proxy Host: prompted.sbs
   - Forward to: localhost:8080 (or static file server)
   - SSL: Request Let's Encrypt certificate

3. Update Cloudflare tunnel to route `prompted.sbs` → Nginx Proxy Manager

## Domain Setup (prompted.sbs)

1. Purchase domain from registrar
2. Update nameservers to Cloudflare:
   - NS1: <cloudflare-ns>.ns.cloudflare.com
   - NS2: <cloudflare-ns>.ns.cloudflare.com

3. DNS Records in Cloudflare:
   ```
   Type: CNAME
   Name: @
   Target: <your-deployment-target>
   Proxy: Enabled (orange cloud)

   Type: CNAME
   Name: www
   Target: prompted.sbs
   Proxy: Enabled
   ```

## Customization

### Updating Content

- **Services**: Edit the `.services-grid` section in `index.html`
- **Technical Skills**: Modify `.expertise-grid` tech tags
- **Contact Email**: Update in both `index.html` and `script.js`
- **Colors**: Adjust CSS variables in `:root` selector in `styles.css`

### Adding Analytics

Add Google Analytics or Plausible before `</head>`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## Performance Optimization

Current optimizations:
- ✅ Minified CSS (can be compressed further)
- ✅ Vanilla JS (no heavy frameworks)
- ✅ Optimized images (emoji icons instead of image files)
- ✅ Lazy loading for scroll animations
- ✅ Font preloading

Future optimizations:
- [ ] Add service worker for offline support
- [ ] Implement image lazy loading if adding photos
- [ ] Add sitemap.xml for SEO
- [ ] Add robots.txt

## Browser Support

- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Android)

## License

Personal portfolio website - All rights reserved.

## Contact

For updates or issues with the website:
- Email: pieter.talboom@gmail.com
