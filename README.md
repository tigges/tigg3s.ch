# tigg3s.ch Services Landing Page

Single-page portal for **tigg3s.ch** users to quickly access Infomaniak services (Mail, kDrive, Manager).

## Deploy to Infomaniak hosting (recommended)

This repository includes a GitHub Actions workflow that can publish the static files to an Infomaniak Web Hosting via **FTPS**:

- Workflow: `.github/workflows/deploy-infomaniak.yml`
- Upload strategy: mirror repository content to the remote web root

### 1) Create / retrieve an FTP(S) account in Infomaniak Manager

In Infomaniak Manager (Web Hosting):

1. Create an FTP user (or use an existing one)
2. Note the **FTP host**, **username**, **password**
3. Confirm the remote web directory (commonly `/web`)

### 2) Add GitHub repository secrets

Add the following **Actions secrets** in GitHub:

- `INFOMANIAK_FTP_HOST` (example: `xxxxxx.ftp.infomaniak.com`)
- `INFOMANIAK_FTP_USER`
- `INFOMANIAK_FTP_PASSWORD`
- `INFOMANIAK_FTP_REMOTE_DIR` (optional; defaults to `/web`)

Push a commit (or re-run the workflow) and the site will be deployed.

## Connect `tigg3s.ch` to the hosting

If `https://tigg3s.ch/` still shows a different site (e.g. “Infomaniak Site Creator”), the domain is not currently serving this hosting directory.

In Infomaniak Manager:

1. Attach `tigg3s.ch` (and optionally `www.tigg3s.ch`) to the correct Web Hosting / site
2. Ensure the site’s document root points to the directory where `index.html` is deployed (typically `/web`)
3. Update DNS to the hosting’s recommended A/AAAA records (if needed)
4. Enable SSL and force HTTPS (the repository provides an `.htaccess` for canonical redirects)

