# audible-cli Cheat Sheet

**Purpose:** Download Audible audiobooks as `.aax` (legacy, DRM-protected, needs auth code) or `.aaxc` (newer, uses `.voucher` for DRM, no auth code). Use `--chapter`, `--cover` and `--annotation` to get `<title>-chapters.json`, `<title>_(500).jpg` and `<title>-annotations.json` for metadata; `.voucher` only contains DRM keys.

**Commands:**
- **Help:** Show all options.
  ```bash
  audible -h
  audible download -h
  ```
- **Login/Setup:** Authenticate with Audible account.
  ```bash
  audible quickstart
  ```
- **Get Auth Code:** Retrieve 8-digit authentication code (needed for AAXtoMP3 .aax file conversion).
  ```bash
  audible activation-bytes
  ```
- **Export Library:** Export complete details of books in library. Default output folder is <Home>/ if -o flag is not used. Default format is .tsv, but .csv and .json are also available.
  ```bash
  audible library export --start-date <YYYY-MM-DD> -o <path_to_output_folder>
  ```
- **Check Library:** List ASINs of owned books. Handy for quick lookup for a single download. **NOTE: ASIN can also be found in book's webpage URL.**
  ```bash
  audible library list --start-date <YYYY-MM-DD>
  ```
- **Download Single Book (.aax):** Downloads `.aax`, JSON, cover. Will fallback to .aaxc if .aax is not available. **NOTE: Output (target) directory must exist if specifying--program will not create new folders.**
  ```bash
  audible download -a <ASIN> --aax-fallback --cover --chapter --annotation -o <path_to_output_folder>
  ```
- **Download Single Book (.aaxc):** Downloads `.aaxc`, `.voucher`, JSON, high-resolution cover. **NOTE: Output (target) directory must exist if specifying--program will not create new folders.**
  ```bash
  audible download -a <ASIN> --aaxc --cover --cover-size 1215 --chapter --annotation -o <path_to_output_folder>
  ```
- **Download Books Added After a Date:** Downloads .aaxc books added to library on or after the specified UTC date. **NOTE: Output (target) directory must exist if specifying--program will not create new folders.**
  ```bash
  audible download --all --aaxc --cover --chapter --annotation --start-date <YYYY-MM-DD> -o <path_to_output_folder>
  ```
  - Example: Books added after May 1, 2025
    ```bash
    audible download --all --aaxc --cover --chapter --ignore-errors --annotation --start-date 2025-05-01 -o ~/Downloads/Audible
    ```
- **Download All Books:** Downloads entire library as `.aaxc`. **NOTE: Output (target) directory must exist if specifying--program will not create new folders.**
  ```bash
  audible download --all --aaxc --chapter --cover --ignore-errors --annotation -o <path_to_output_folder>
  ```
