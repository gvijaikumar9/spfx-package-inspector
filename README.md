# SPFx Package Inspector

Check a SharePoint Framework (SPFx) package before you approve it.

Drop an `.sppkg` file into the page and get a report on:

- **API permission requests**: every Microsoft Graph or custom API scope in `webApiPermissionRequests`, rated High, Medium or Low by how much data it reaches.
- **Domains in the code**: hosts found in the shipped JavaScript, grouped as Microsoft, third-party, or documentation links.
- **Deployment scope**: whether the package can be made available to all sites, extensions that switch on across sites, and code loaded from a CDN instead of the package.
- **Secrets and keys**: strings shaped like Entra ID client secrets, Azure Storage keys, SAS tokens, private keys, AWS, GitHub and Slack tokens. Values are masked in the report.
- **Components**: every web part, extension and library, with ID, version and supported hosts.
- **Bundle hygiene**: bundle size, shipped source maps, and old build files that no component references.

You can export the report as Markdown or JSON.

**Use it online:** https://tools.fivenumber.com/spfx-package-inspector/

## Privacy

The package never leaves your browser. The page unzips it in the tab with the browser's built-in `DecompressionStream` and runs every check locally. Nothing is uploaded and there is no backend.

## Run it yourself

It is a single static HTML file with no dependencies and no build step.

- Open `index.html` in a current version of Edge, Chrome, Firefox or Safari, or
- Serve the folder with any static web server.

This copy is the same page that runs on tools.fivenumber.com, without the site's analytics tags. The IBM Plex font files are not included, so it falls back to your system font.

## Who needs what permission

None. The tool reads a file you already have. To get an `.sppkg` from your tenant you need read access to the app catalog site, or you can get the file from the developer or vendor.

## Limits

This is static analysis. A clean report does not prove a package is safe, and a finding does not prove it is malicious. Use the report to decide what to ask the developer or vendor. Domains are found as text in the code; they are not observed as network calls. ZIP64 packages are not supported yet.

## Feedback and issues

Open an issue for a false positive or a check you would like added. Please do not attach packages that contain confidential code.

## License

MIT. See [LICENSE](LICENSE).

Microsoft, SharePoint, Microsoft 365 and Entra are trademarks of the Microsoft group of companies. This project is not affiliated with or endorsed by Microsoft.
