# Leo's Coffee Website - Quick Start Guide

## 🚀 View the Live Website

**The website is already live and deployed!**

**Live URL:** https://f246632.github.io/168_Leo-s-Coffee/

Simply open this URL in any web browser to see the complete website.

---

## 💻 Local Preview (Optional)

If you want to view or edit the website locally on your computer:

### Option 1: Direct File Opening (Simple)

1. Navigate to the project folder:
   ```
   /Users/m./berlinwebsites/168_Leo's Coffee
   ```

2. Double-click `index.html` to open in your default browser

3. **Note:** Some features (like contact form) work better with a local server

### Option 2: Local Web Server (Recommended)

Choose one of these methods:

#### A) Using Python (if installed)

```bash
cd "/Users/m./berlinwebsites/168_Leo's Coffee"

# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

Then open: http://localhost:8000

#### B) Using Node.js (if installed)

```bash
cd "/Users/m./berlinwebsites/168_Leo's Coffee"
npx http-server
```

Then open: http://localhost:8080

#### C) Using PHP (if installed)

```bash
cd "/Users/m./berlinwebsites/168_Leo's Coffee"
php -S localhost:8000
```

Then open: http://localhost:8000

#### D) Using VS Code

1. Install "Live Server" extension
2. Right-click `index.html`
3. Select "Open with Live Server"

---

## 📱 Testing on Mobile Devices

### Local Network Testing

1. Start a local server (see above)
2. Find your computer's IP address:
   ```bash
   # macOS/Linux
   ifconfig | grep "inet "

   # Windows
   ipconfig
   ```
3. On your mobile device, visit: `http://YOUR_IP_ADDRESS:8000`

### Live Website Testing

Simply visit the live URL on your mobile device:
https://f246632.github.io/168_Leo-s-Coffee/

---

## 🛠️ Making Edits

### Quick Text Changes

1. Open `index.html` in any text editor
2. Find the section you want to edit
3. Make your changes
4. Save the file
5. Refresh your browser to see changes

### CSS Style Changes

1. Open `css/style.css`
2. Find the relevant style (use browser DevTools to identify)
3. Make your changes
4. Save and refresh

### JavaScript Changes

1. Open `js/main.js`
2. Edit the functionality
3. Save and refresh

### Committing Changes to GitHub

```bash
cd "/Users/m./berlinwebsites/168_Leo's Coffee"
git add .
git commit -m "Description of your changes"
git push
```

Changes will appear on the live site in 1-2 minutes.

---

## 📂 Project Structure at a Glance

```
leo's-coffee/
├── index.html           ← Main website file (EDIT THIS for content)
├── css/
│   └── style.css       ← Styles (EDIT THIS for design)
├── js/
│   └── main.js         ← Interactivity (EDIT THIS for functionality)
├── images/
│   └── source/         ← 10 café photos
├── README.md           ← Full documentation
├── DEPLOYMENT.md       ← Deployment details
└── QUICKSTART.md       ← This file
```

---

## 🎨 Common Edits

### Update Opening Hours

**File:** `index.html`
**Search for:** "Öffnungszeiten" or "Opening Hours"
**Lines:** ~512-520

```html
<table class="hours-table">
    <tr>
        <td>Montag - Samstag</td>
        <td>08:00 - 17:00</td>  <!-- EDIT THIS -->
    </tr>
    <tr>
        <td>Sonntag</td>
        <td>10:00 - 17:00</td>  <!-- EDIT THIS -->
    </tr>
</table>
```

### Update Phone Number

**File:** `index.html`
**Search for:** "+49 30 50593889"
**Replace all instances** with new number

### Update Menu Items

**File:** `index.html`
**Search for:** "menu-item"
**Example:**

```html
<div class="menu-item">
    <div class="item-header">
        <h4>Espresso</h4>
        <span class="price">€2.50</span>  <!-- EDIT PRICE -->
    </div>
    <p class="item-description">Klassischer italienischer Espresso</p>  <!-- EDIT DESCRIPTION -->
</div>
```

### Add New Menu Item

Copy an existing menu item block and modify:

```html
<div class="menu-item">
    <div class="item-header">
        <h4>Your New Item</h4>
        <span class="price">€X.XX</span>
    </div>
    <p class="item-description">Description of your item</p>
</div>
```

### Change Colors

**File:** `css/style.css`
**Lines:** 8-30 (CSS Variables section)

```css
:root {
    --color-primary: #3E2723;      /* Dark Espresso - EDIT THIS */
    --color-secondary: #FF6F00;     /* Warm Orange - EDIT THIS */
    --color-accent: #D7CCC8;        /* Cream - EDIT THIS */
}
```

---

## 🔍 Finding Specific Content

Use your text editor's search function (Ctrl+F or Cmd+F):

| To find... | Search for... |
|------------|--------------|
| Opening hours | "Öffnungszeiten" |
| Menu items | "menu-item" |
| Phone number | "+49 30" |
| Address | "Greifswalder" |
| Instagram | "@leoscoffeeberlin" |
| Gallery images | "gallery-item" |
| Reviews | "review-card" |

---

## ✅ Checklist After Making Changes

- [ ] Save all edited files
- [ ] Refresh browser to check changes
- [ ] Test on mobile (resize browser window)
- [ ] Check for typos
- [ ] Verify all links still work
- [ ] Commit to Git (if satisfied)
- [ ] Push to GitHub (to update live site)

---

## 🆘 Troubleshooting

### Images Not Loading

**Problem:** Images show broken link icon
**Solution:**
1. Check image file exists in `images/source/`
2. Verify image filename matches HTML (case-sensitive)
3. Use relative path: `images/source/filename.jpg`

### Changes Not Appearing

**Problem:** Edits don't show on website
**Solution:**
1. Hard refresh browser (Ctrl+Shift+R or Cmd+Shift+R)
2. Clear browser cache
3. Make sure you saved the file
4. Check correct file was edited

### GitHub Pages Not Updating

**Problem:** Live site doesn't show latest changes
**Solution:**
1. Verify changes were pushed to GitHub
2. Wait 1-2 minutes for rebuild
3. Check GitHub Actions for build status
4. Hard refresh browser cache

### Contact Form Not Working

**Problem:** Form submission doesn't work
**Solution:**
This is expected - the form needs backend setup. Current version shows success message but doesn't actually send emails. To fix:
1. Use a service like Formspree, Netlify Forms, or EmailJS
2. Or add backend email handling

---

## 📞 Getting Help

### Documentation

- **Full Guide:** See `README.md` for complete documentation
- **Deployment Info:** See `DEPLOYMENT.md` for deployment details
- **Technical Specs:** See `docs/architecture.md`

### GitHub Repository

**URL:** https://github.com/f246632/168_Leo-s-Coffee

- View code online
- Report issues
- Track changes
- Collaborate with others

### Quick Links

- **Live Website:** https://f246632.github.io/168_Leo-s-Coffee/
- **Instagram:** https://instagram.com/leoscoffeeberlin
- **Google Maps:** [View on Maps](https://www.google.com/maps/search/?api=1&query=Leo's%20Coffee&query_place_id=ChIJ7wgynmRPqEcR7AKn4n7ae_A)

---

## 🎯 Next Steps

### For Café Owner

1. **Review** - Check website for accuracy
2. **Share** - Post on Instagram and social media
3. **Update** - Add to Google Business listing
4. **Print** - Add URL to business cards/menus
5. **Promote** - Tell customers about new website

### For Developers

1. **Optimize Images** - Convert to WebP format
2. **Add Analytics** - Set up Google Analytics
3. **Email Setup** - Configure contact form backend
4. **SEO** - Submit sitemap to Google
5. **Enhancement** - See DEPLOYMENT.md for roadmap

---

**That's it! You're all set to view and edit Leo's Coffee website.**

**Live Site:** https://f246632.github.io/168_Leo-s-Coffee/

**Enjoy!** ☕