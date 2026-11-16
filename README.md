# rheysoft.github.io

Source of the website rheysoft.com: the landing page, the Impressum, the general privacy policy (German and English) and the privacy policies of individual products.

## Public repository, live branch

This repository is public, including its complete history. The branch `main` is published by GitHub Pages to rheysoft.com. Every push to `main` goes live immediately, so changes are prepared on separate branches and merged into `main` only when they are ready to be published.

## Preview locally

The pages are static HTML with root-relative paths (for example `/fonts.css`), so serve them from the repository root:

```bash
python -m http.server 8000
```

Then open http://localhost:8000/. Extensionless links such as `/datenschutz` or `/privacy` only resolve on GitHub Pages; locally, open the `.html` file instead.

## Publishing

Pushing to `main` triggers the GitHub Pages build and publishes the site at rheysoft.com. `_config.yml` keeps repository files such as this README and the LICENSE out of the published site.

## Domain and DNS

The site is served at rheysoft.com by GitHub Pages from this repository. The domain is registered at Namecheap, and its DNS records are held there, not at GitHub.

### Current records

| Type | Host | Value | Purpose |
|---|---|---|---|
| A | @ | 185.199.108.153 | GitHub Pages |
| A | @ | 185.199.109.153 | GitHub Pages |
| A | @ | 185.199.110.153 | GitHub Pages |
| A | @ | 185.199.111.153 | GitHub Pages |
| CNAME | www | rheysoft.github.io | GitHub Pages for www.rheysoft.com |
| MX | @ | eforward1.registrar-servers.com (10), eforward2.registrar-servers.com (10), eforward3.registrar-servers.com (10), eforward4.registrar-servers.com (15), eforward5.registrar-servers.com (20) | Namecheap email forwarding |
| TXT | @ | `v=spf1 include:spf.efwd.registrar-servers.com ~all` | SPF for the forwarding |
| NS | @ | dns1.registrar-servers.com, dns2.registrar-servers.com | Authoritative nameservers (Namecheap) |

Email forwarding is configured at the registrar; aliases and destination addresses are intentionally not documented here.

### Registrar and where DNS is edited

- Registrar: Namecheap. The account is owned by the company. Account names and payment details are not documented here.
- DNS records are edited in the Namecheap dashboard under Domain List -> Manage -> Advanced DNS. GitHub does not hold or edit the DNS records.

### GitHub Pages settings

- Repository Settings -> Pages: source branch `main`, folder `/` (legacy build, no workflow).
- Custom domain: `rheysoft.com`. Enforce HTTPS: on.
- The file `CNAME` in the repository root must contain `rheysoft.com`. Do not delete or rename it; the branch build takes the custom domain from it.
- The HTTPS certificate covers rheysoft.com and www.rheysoft.com and is issued and renewed by GitHub automatically.
- Recommended: verify rheysoft.com under Verified domains in the GitHub account settings to protect it against takeover.

### Domain renewal

- The domain renews on 18.04.2027. Auto-renew is enabled at the registrar and stays enabled.
- Before that date, check in the Namecheap dashboard that auto-renew is still on and the payment method on file is valid. After the renewal, check the new expiry date and run the checks under Verify.

### Moving DNS or changing the Pages source

- Moving DNS to another provider: recreate every record from the table at the new provider before switching the nameservers at the registrar. This includes the MX and SPF records; otherwise email forwarding stops. Then run the checks under Verify.
- Changing the Pages source (another branch, another folder or a deploy workflow): keep the custom domain `rheysoft.com` and Enforce HTTPS in the Pages settings, keep the `CNAME` file, then run the checks under Verify.

### Verify

Run these against a public resolver and compare the output with the table above. The last command needs a GitHub CLI login with access to this repository.

```bash
nslookup -type=A rheysoft.com 8.8.8.8
nslookup -type=CNAME www.rheysoft.com 8.8.8.8
nslookup -type=NS rheysoft.com 8.8.8.8
nslookup -type=MX rheysoft.com 8.8.8.8
nslookup -type=TXT rheysoft.com 8.8.8.8
gh api repos/rheysoft/rheysoft.github.io/pages
```

Last verified: 16.11.2026 (DNS via 8.8.8.8, Pages settings via the GitHub API).

## Owner and licence

The content belongs to rheysoft UG (haftungsbeschränkt). It is proprietary; see [LICENSE](LICENSE).

## Contact

rheysoft@gmail.com
