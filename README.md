# adddots.com

The Add Dots studio website: plain HTML, no build step. Every push to `main` uploads the site to Hostinger automatically ([.github/workflows/deploy.yml](.github/workflows/deploy.yml)). You can also upload the files by hand (Hostinger → File Manager → public_html), keeping the same folders.

Only the home page sits directly in public_html, next to the subdomain folders (call/, pdf/, opbuilder/). Everything else is in `adddotsmain/`:

- `index.html`: home page
- `adddotsmain/about.html`: About, with the founder card
- `adddotsmain/optionbuilder/index.html`: AddStock (formerly Option Builder), the Products menu's page for it, with its screenshots in `adddotsmain/optionbuilder/img/`. Its Windows buttons are placeholders (`href="#"`) until the app is on the Microsoft Store
- `adddotsmain/pdf/index.html`: PDF Reader + Editor (Add Dots PDF), the Products menu's page for it, with its screenshots in `adddotsmain/pdf/img/`
- `adddotsmain/addcall/index.html`: Add Call, the page both Products → Add Call and Applications → Add Call · Android open: short headlines over its screenshots (in `adddotsmain/addcall/img/`), with Google Play, the Download APK button, the web app and placeholder Windows buttons (`href="#"`) until it is on the Microsoft Store
- `adddotsmain/addcall/add-call.apk`: the Android app. Not in this repository (ignored by .gitignore). Upload the newest signed APK here under this exact name, and the button picks it up.

The Applications menu (after Products) lists Add Call. When there's a new app version, update the `V1.1` badge in the menus of every page and the "Version 1.1" line on the Add Call page.

## Automatic upload: one-time setup

1. hPanel → **Files → FTP Accounts**: use the account whose directory is `/home/…/domains/adddots.com/public_html` (`u858015397.main`) and set its password. Not the main `u858015397` login, which opens in the home folder.
2. GitHub → this repository → **Settings → Secrets and variables → Actions → New repository secret**, three times:
   - `FTP_SERVER`: `ftp.adddots.com`
   - `FTP_USERNAME`: the FTP username
   - `FTP_PASSWORD`: its password
3. Don't add `FTP_SERVER_DIR`. The deploy stops with an error if the login doesn't open in the live site folder (it looks for the `call` folder of call.adddots.com there).
4. **Actions → Deploy → Run workflow** to upload now. After that, every change to `main` goes live on its own.
