# adddots.com

The Add Dots studio website: plain HTML, no build step. Every push to `main` uploads the site to Hostinger automatically ([.github/workflows/deploy.yml](.github/workflows/deploy.yml)). You can also upload the files by hand to the site's root folder (Hostinger → File Manager → public_html).

- `index.html`: home page
- `about.html`: About, with the founder card
- `addcall/index.html`: Add Call for Android, with the Download APK button
- `addcall/add-call.apk`: the Android app. Not in this repository (ignored by .gitignore). Upload the newest signed APK here under this exact name, and the button picks it up.

The Applications menu (after Products) lists Add Call. When there's a new app version, update the `V1.1` badge in the menus of all three pages and the version on the Add Call page.

## Automatic upload: one-time setup

1. hPanel → **Files → FTP Accounts**: use the account whose directory is `/home/…/domains/adddots.com/public_html` (`u858015397.main`) and set its password. Not the main `u858015397` login, which opens in the home folder.
2. GitHub → this repository → **Settings → Secrets and variables → Actions → New repository secret**, three times:
   - `FTP_SERVER`: `ftp.adddots.com`
   - `FTP_USERNAME`: the FTP username
   - `FTP_PASSWORD`: its password
3. Don't add `FTP_SERVER_DIR`. The deploy stops with an error if the login doesn't open in the live site folder (it looks for the `call` folder of call.adddots.com there).
4. **Actions → Deploy → Run workflow** to upload now. After that, every change to `main` goes live on its own.
