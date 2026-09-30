# Contributing a translation

1. Clone the main QDirStat repo and generate the current `.pot`:
```bash
   git clone https://github.com/shundhammer/qdirstat.git
   cd qdirstat/src
   ./makepot
```

2. **New language:** create your `.po` from the `.pot`:
```bash
   msginit --input=qdirstat.pot --locale=<your_locale> --output=<your_locale>.po
```

   **Updating an existing translation:** sync your `.po` with the latest `.pot`:
```bash
   msgmerge --update --backup=off <your_locale>.po qdirstat.pot
```

3. Translate the strings (e.g. with [Poedit](https://poedit.net/)). For keyboard accelerators (`&`), keep the same key where possible; for CJK languages, appending `(&X)` after the translated text is the standard convention.

4. Validate before submitting:
```bash
   msgfmt --check --check-format <your_locale>.po
```

5. To test locally: compile the `.po` to `.mo` and copy it to `/usr/share/locale/<your_locale>/LC_MESSAGES/qdirstat.mo`.

   Note: if you've run QDirStat before, delete or rename the existing config files in `~/.config/QDirStat/` (`QDirStat.conf`, `QDirStat-cleanup.conf`, `QDirStat-mime.conf`, `QDirStat-exclude.conf`) so the default cleanup actions and MIME categories get re-seeded under your locale — otherwise they'll keep showing in English even after switching.

6. Open a pull request here with your `.po` file under `po/`.
