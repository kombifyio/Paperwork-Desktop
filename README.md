# Paperwork for Windows (beta installers)

This repository hosts the Windows installers of
[Paperwork](https://paperwork.kombify.io) by kombify. It contains release
metadata and binary installers only. The source code is not published here.

## Download

Every version is a GitHub release with the tag `windows-v<VERSION>`. It
contains:

- `Paperwork-<VERSION>-x64.msi`: the installer (per machine, Windows 10/11 x64)
- `SHA256SUMS.txt` and `Paperwork-<VERSION>-x64.msi.sha256`: checksums
- `paperwork-windows-v<VERSION>-receipt.json`: the release receipt (version,
  asset digests, source revision)
- `UNSIGNED-WINDOWS-RELEASE.txt` and `THIRD-PARTY-NOTICES.md`

The release `windows-beta` always carries `paperwork-windows-beta.json`, the
signed update manifest that installed copies of Paperwork read to find the
current beta version.

## Unsigned beta

The installers are intentionally not Authenticode-signed, so Windows
SmartScreen may warn before the first start. Verify the download against its
checksum instead:

```powershell
(Get-FileHash .\Paperwork-<VERSION>-x64.msi -Algorithm SHA256).Hash.ToLower()
```

The result must equal the value in `SHA256SUMS.txt` of the same release.
Installed copies of Paperwork verify updates themselves: they accept only an
update manifest with a valid Ed25519 signature, and they check the size and
SHA-256 of the installer before it runs.

## Support

Use Paperwork itself or https://paperwork.kombify.io for help. This
repository does not accept issues or pull requests.
