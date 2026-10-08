# BitBullGold Website

Official download website for BitBullGold, a local-first Solana market-scanning and controlled-trading desktop application for Windows.

## Website features

- Responsive desktop and mobile design
- BitBullGold product overview
- Trading and wallet safety information
- Windows system requirements
- X follow-and-download flow
- GitHub and Vercel compatible
- No build tools or external dependencies required

## Configure the website

Open `index.html` and locate:

```javascript
window.BITBULLGOLD_CONFIG = {
  xProfileUrl: "https://x.com/your_account",
  downloadUrl: "https://github.com/solanatradingplatform/solana-trading-platform/releases/latest",
  releaseVersion: "Current Windows release",
  downloadLabel: "Download for Windows"
};
```

Replace `your_account` with the actual BitBullGold X username.

When the Windows installer is published as a GitHub release, replace `downloadUrl` with its direct release asset URL:

```text
https://github.com/OWNER/REPOSITORY/releases/download/VERSION/BitBullGold-Setup-x64.exe
```

Do not place passwords, API keys, X client secrets, wallet files, environment files or private keys inside `index.html`.

## X follow verification

The current website asks visitors to open the BitBullGold X profile and confirm that they followed it.

This is a confirmation-based gate. A static HTML website cannot securely verify whether a visitor followed an X account.

Verified follow enforcement will require:

1. An X developer account and approved API access
2. X OAuth 2.0 user authentication
3. A Vercel serverless API endpoint
4. Server-side follow-relationship verification
5. A protected or short-lived installer download URL

X client secrets must be stored as Vercel environment variables and never included in browser code.

## Preview locally

You can double-click `index.html`, or serve it locally with Python:

```powershell
Set-Location "$env:USERPROFILE\BitBullGold-Website"
python -m http.server 8080
```

Open:

```text
http://127.0.0.1:8080
```

## Publish to GitHub

Create a new repository, such as:

```text
bitbullgold-website
```

From PowerShell:

```powershell
Set-Location "$env:USERPROFILE\BitBullGold-Website"

git init
git add index.html README.md
git commit -m "Add BitBullGold website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/bitbullgold-website.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

## Deploy with Vercel

1. Sign in to Vercel.
2. Select **Add New → Project**.
3. Import the `bitbullgold-website` GitHub repository.
4. Choose **Other** as the framework preset.
5. Leave the build command empty.
6. Set the output directory to `.`.
7. Select **Deploy**.

Vercel will redeploy the website when changes are pushed to the connected production branch.

## System requirements

- Windows 10 or Windows 11
- 64-bit x64 processor
- Reliable internet connection
- Local wallet created after installation

## Security

The website must never contain or distribute:

- `.env` files
- `wallet.enc`
- Wallet passwords
- Private keys or recovery phrases
- `platform.db`
- Logs containing sensitive information
- GitHub or X access tokens

Only the signed or approved BitBullGold installer should be published for download.

## Risk notice

Trading digital assets involves substantial financial risk. BitBullGold’s safety controls cannot eliminate market, liquidity, slippage, execution or software risk. Users are responsible for reviewing settings and understanding the risks before enabling live trading.

## License

All rights reserved unless a separate license is added to this repository.
