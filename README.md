# Pancham Hardware and Electricals — Inventory

A mobile-first, static offline inventory PWA designed for GitHub Pages.

## Included features
- Product create/edit and search by name, brand, SKU, category, or notes
- Category and brand filters
- Cost price, selling price, discount, stock quantity, SKU and notes
- Live discounted price, adjusted profit per unit, and profit margin
- Dashboard totals for unique products, categories, stock cost value and potential profit
- Device-local storage, JSON backup export and restore
- PIN lock with hashed PIN stored in the browser
- PWA manifest and service worker for offline loading after first visit

## Deploy to GitHub Pages
1. Extract the ZIP.
2. Upload the contents of this folder to the root of the repository used by your GitHub Pages site.
3. Commit and push the changes.
4. In GitHub, open **Settings → Pages** and confirm the intended branch/folder is published.
5. Open the published site while online once, then use **Add to Home screen** in Chrome.

If your Pages site is configured to publish from `/docs` instead of the repository root, upload these files to that configured folder instead.

## Important limitations
- This is a starter implementation that uses browser localStorage, not a secure encrypted database. The PIN lock is a convenience lock and should not be treated as strong device-level security. Anyone with access to browser developer tools or the browser profile may be able to access locally stored inventory.
- Data is local to a browser profile/device. Export a JSON backup regularly. Restoring replaces current inventory after confirmation.
- Google Drive backup is not enabled in this static starter because it requires Google Cloud OAuth setup, a valid OAuth client ID, consent configuration and authorized redirect/origin settings. Do not paste client secrets into browser code. A production version should add a reviewed Drive integration and encrypted backup workflow.
- The service worker can cache the app shell, but first load and installation require internet. Browser storage can be cleared by the device or browser; keep backups.
- Before real shop use, test backup/restore and protect the device with Android screen lock.

## Data calculations
- Discounted selling price = selling price × (1 − discount% / 100)
- Adjusted profit per unit = discounted selling price − cost price
- Profit margin = adjusted profit / discounted selling price × 100
- Potential profit on dashboard uses undiscounted selling price minus cost, multiplied by stock quantity.

## Shop logo
Your supplied gold lotus-style logo is included as `logo.png` and appears on the app header, PIN-lock screen, and install icon. Keep `logo.png` alongside `index.html` when deploying.
