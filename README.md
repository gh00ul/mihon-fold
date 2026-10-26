# Mihon Fold

Mihon with automatic two-page spreads when a book-style foldable is unfolded, and one page when it's folded. It installs as a separate app, "Mihon Fold" (`app.mihon.fold`), with no telemetry.

## How updates work
Every day, the workflow checks Mihon's `main` branch. When there's a new commit, it applies `mihon-fold.patch`, builds the APK and publishes it as a GitHub release. Obtainium on your phone picks up that release and updates the app.

If Mihon changes the code the patch edits, the build fails and GitHub emails you. Your installed app keeps working; only the patch needs updating.

## One-time setup (all from your phone)
1. Create a GitHub repo, which can be public, and add the files from this folder at the same paths: `mihon-fold.patch`, `README.md`, `.github/workflows/build.yml`.
2. Go to **Settings → Secrets and variables → Actions → New repository secret** and add two secrets:
   - `KEYSTORE_BASE64`: paste the contents of `KEYSTORE_BASE64.txt`
   - `KEY_PASSWORD`: paste the contents of `KEY_PASSWORD.txt`
3. Go to **Actions**, enable workflows if asked, then open **Build Mihon Fold → Run workflow** once.
4. In **Obtainium**, choose **Add app**, paste your repo's URL, and save. It installs and updates Mihon Fold from your releases.

Never upload the `secrets-do-not-upload` folder. Keep it somewhere safe, because the same key lets new builds install over your current one.

GitHub pauses daily runs after 60 days without commits to the repo, and emails you before it does. Re-enable them with one tap in Actions.
