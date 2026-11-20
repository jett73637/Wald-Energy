# GitHub setup

Repository: `jett73637/Wald-Energy`

Recommended settings:
- Visibility: Public (so the ESP can download release assets without a GitHub token).
- Default branch: `main`.
- Do not enable Pages or Actions merely for hosting release binaries.
- Do not store secrets in repository files or commit history.

## Upload from a phone

1. Extract `Wald-Energy-Repository-Scaffold.zip` on the phone.
2. Open the repository on github.com.
3. Choose **Add file → Upload files**.
4. Upload the contents of the extracted `Wald-Energy-Repository` folder (including hidden `.gitignore` if the file picker allows it).
5. Commit to `main`.

If the mobile browser cannot select a whole folder, upload the ZIP itself as an archive or use GitHub's desktop site / a Git client. GitHub's web upload interface may not preserve empty directories; `.gitkeep` files are included for that reason.
