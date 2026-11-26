# 🐟 Fish Tank Map – 더조은수산

A mobile-friendly map of the farm's tanks (1동 / 2동 / 3동) showing how many fish are in each tank.
The boss opens the link on a phone to see it. The admin updates it from a phone.

- **Boss / viewers:** open the link. It shows:
  - the map and totals
  - delivery-ready tanks (🚚), empty tanks and hospital tanks (🏥)
  - daily deaths and medicine losses for the last 7 days
  - the change history

  The page refreshes every minute.
- **Admin:** tap **관리 / Admin** and log in with **admin / admin**. Then:
  - Tap **📋 일일 폐사 입력 / Daily loss entry** once a day:
    - **💀 Deaths:** enter one number for the whole farm. It comes off the farm total, not off a tank.
    - **💊 Medicine:** these fish stay on the farm and move into a 🏥 hospital tank. Choose the tank they came from, or "Unknown" if you don't know.
    - The report at the bottom of the page shows deaths today, this month and in total, the fish in hospital tanks, and a day-by-day table.
    - After a full recount of every tank, use **전체 재계수 완료 / Full recount done** to reset the deaths/moves that were not taken off a tank.
  - Tap any tank to:
    - reduce the count (died / medicine / sold), with quick −1 / −5 / −10 / −20 / −50 / −100 buttons
    - mark it 🚚 **delivery ready**, or ✅ **harvested → empty tank**
    - mark it 🏥 **hospital tank**, or give it a name label (for example 치어 or 격리)
    - restock, add fish, move fish to another tank, set the exact count, or add a note

Every change is saved as a commit to `data.json` in this repo, so a full history is kept.

---

## 1. Put it on GitHub (one time)

1. Go to https://github.com/new and create a repository, for example `fish-farm` (Public).
2. Unzip `fish-farm-upload.zip`. On the new repo page, click **uploading an existing file**. Drag in **everything inside** the unzipped folder: `index.html`, `data.json`, `README.md`, `.nojekyll` and the `images` folder. Then click **Commit changes**.
3. In the repo, open **Settings → Pages**. Under **Branch**, choose `main` and `/ (root)`, then click **Save**.
4. After about 1 minute the site is live at:
   **`https://YOUR-USERNAME.github.io/fish-farm/`**
   Send this link to the boss. (On the phone: Share → **Add to Home screen** to use it like an app.)

## 2. Make the GitHub token (one time per admin phone)

1. Open https://github.com/settings/personal-access-tokens/new (Fine-grained token).
2. Name: `fish-map`. Expiration: choose what you like (for example 1 year).
3. **Repository access → Only select repositories →** choose `fish-farm`.
4. **Permissions → Repository permissions → Contents → Read and write.**
5. Click **Generate token** and copy it (`github_pat_…`).
6. On your phone, open the site → **관리 / Admin** → log in with admin / admin. The first time, the setup screen opens. Paste the token there and tap **Save & check**.
   The username and repository name are filled in automatically.

After that, logging in with admin / admin is all you need on that phone.

## Security notes

- The **admin / admin** login only hides the admin screens. Anyone can read the page source, so it is not real protection.
  **Saving is protected by the GitHub token**, and the token is stored only on the admin's phone. A phone without the token cannot change anything.
- To change the password, put the SHA-256 of the new password into `ADMIN_PASS_SHA256` in `index.html`. You can make one at https://emn178.github.io/online-tools/sha256.html.
- Do not send the token to anyone. If a phone is lost, delete the token on GitHub.

## Changing the layout

The tank positions are in `index.html` → `const LAYOUT = [...]` (`c` = column, `r` = row).
The starting numbers were entered from the handwritten sheet of 2026-11-13 (`images/floor-plan.jpg`).
