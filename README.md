# InvoiceShelf (LazyCat LPK)

Invoicing and expense management.

- Upstream: https://github.com/InvoiceShelf/InvoiceShelf (branch `3.x`)
- Image: `invoiceshelf/invoiceshelf:2.4.7` (mirror mode, digest-matched)
- License: AGPL-3.0 (full text in `content/licenses/LICENSE`)
- Containers: single (SQLite)

## Notes

- Upstream's `InvoiceShelf/docker` compose ships an SQLite variant:
  `DB_CONNECTION=sqlite` + `DB_DATABASE=/var/www/html/storage/app/database.sqlite`.
  So this stays single-container.
- First-run wizard: `app/Platform/Operations/Installation/` has `OnboardingWizardController`
  guarded by `UseInstallWizardTokenAuth` + `InstallWizardAuth`. The "token" is just the header
  pair `X-Install-Wizard: 1` (a marker, not a secret); real gating is `installationIsIncomplete()`.
  The admin account is created in the browser — no seeded credential.
- `APP_KEY` comes from a platform stable secret.
- Persisted dirs: `/var/www/html/storage/` and `/var/www/html/Modules/`.
- No mail service configured.
- Not yet verified on a real device.
