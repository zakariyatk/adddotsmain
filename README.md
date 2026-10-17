# adddots.com

The Add Dots studio website: plain HTML, no build step. Every push to `main` uploads the site to Hostinger automatically ([.github/workflows/deploy.yml](.github/workflows/deploy.yml)). You can also upload the files by hand to the site's root folder (Hostinger → File Manager → public_html).

- `index.html`: home page
- `about.html`: About, with the founder card
- `addcall/index.html`: Add Call for Android, with the Download APK button
- `addcall/add-call.apk`: the Android app. Not in this repository (ignored by .gitignore). Upload the newest signed APK here under this exact name, and the button picks it up.

The Applications menu (after Products) lists Add Call. When there's a new app version, update the `V1.1` badge in the menus of all three pages and the version on the Add Call page.

## Automatic upload: one-time setup

1. hPanel → **Files → FTP Accounts**: note the **FTP host** and the main account's **username**, or create a new account whose directory is `public_html`, and set a password.
2. GitHub → this repository → **Settings → Secrets and variables → Actions → New repository secret**, three times:
   - `FTP_SERVER`: the FTP host, for example `ftp.adddots.com` or the IP shown in hPanel
   - `FTP_USERNAME`: the FTP username
   - `FTP_PASSWORD`: its password
3. If the FTP account opens one level above the site (you see `public_html` when you connect), add a variable instead of a secret on the **Variables** tab: `FTP_SERVER_DIR` = `public_html/`.
4. **Actions → Deploy → Run workflow** to upload now. After that, every change to `main` goes live on its own.
