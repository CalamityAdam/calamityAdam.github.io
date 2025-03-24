## 🌐 Custom Domain Setup (adumb.dev)

This domain is hosted on GitHub Pages and managed via Cloudflare DNS.
The domain was originally registered via Google Domains, then transferred to Squarespace after the migration.

### ⚙️ How it works

- adumb.dev points to GitHub Pages using 4 A records (GitHub's IPs)
- DNS is fully managed by Cloudflare, which allows:
  - CNAME flattening at the apex (root domain) — something Squarespace DNS doesn’t support
  - HTTPS + SSL cert provisioning (via GitHub + Let’s Encrypt)
  - Performance optimizations and caching (optional)
- GitHub Pages requires domain ownership verification via CNAME, which Cloudflare enables with its DNS features

### 🛠️ Where to make changes
| Task                             | Where to go                                                 |
|----------------------------------|--------------------------------------------------------------|
| Domain registration/renewal      | [Squarespace](https://account.squarespace.com)              |
| DNS record changes (A/CNAME)     | [Cloudflare Dashboard](https://dash.cloudflare.com)         |
| GitHub Pages config + HTTPS      | GitHub repo → Settings → Pages                              |
| Set up redirects (www → root)    | Cloudflare → Rules → Page Rules                             |


### 📁 DNS records in Cloudflare

```
A     @      185.199.108.153 (GitHub Pages)
A     @      185.199.109.153
A     @      185.199.110.153
A     @      185.199.111.153
CNAME www    calamityadam.github.io
```


### 📄 CNAME file in repo

```
adumb.dev
```
