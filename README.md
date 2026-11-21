# NinFit v2

An installable, local-first iPhone workout PWA. No build tools required.

## Publish on GitHub Pages
1. Create a GitHub repository named `ninfit` (public is simplest for GitHub Pages).
2. Upload **the contents of this folder** to the repository root: `index.html`, `manifest.webmanifest`, `sw.js`, and both icon PNG files. README is optional.
3. Open repository **Settings → Pages → Build and deployment**. Select **Deploy from a branch**, `main`, `/ (root)`, then Save.
4. When deployment completes, open `https://YOUR-USERNAME.github.io/ninfit/` in iPhone Safari.
5. Share → Add to Home Screen → Add.

## Data safety
- Workout data is stored in the installed app's local IndexedDB. It does **not** sync with GitHub or other devices.
- In Settings, use **Export JSON** regularly and save it to iCloud Drive or Files. **Restore JSON** replaces the entire local database, including templates. CSV is for viewing, not restoration.
- Do not commit JSON backups to a public repository.
- If upgrading from NinFit v1 on the **same origin/browser storage**, v2 attempts a one-time import from the v1 `localStorage` key. Always export a v1 backup before upgrading. This is a best-effort migration, not a guarantee.
- Offline availability requires a successful first online load so the service worker can cache the files. Timer may pause visually when backgrounded but catches up from elapsed time when reopened.

## Implementation notes
- The four day templates are starting defaults based on the previously discussed trainer routine. Check exercises and targets against the latest trainer sheet.
- Template edits affect future sessions; started sessions are independent snapshots.
- This build uses prompt dialogs for editing exercise details. An inline editor is a future polish improvement.
- The app doesn't collect personal information or send workout data to a server.
