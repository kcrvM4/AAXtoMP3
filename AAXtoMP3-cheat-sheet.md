# AAXtoMP3 Cheat Sheet

**Purpose:** Convert `.aax`/`.aaxc` to `.m4a`/`.mp3`/`.flac`/`.opus` with metadata/chapters. `.aax` requires auth code; `.aaxc` uses `.voucher`.

**Commands:**
- **Help:** Show all options.
  ```bash
  AAXtoMP3 -h
  ```
- **Convert Single Book (AAC, .aax):** Converts to `.m4a` with metadata/chapters.
  ```bash
  AAXtoMP3 -a -A <your_code> --use-audible-cli-data -t <path_to_output_folder> <path_to_input_file.aax>
  ```
  - Example: Audiobook-LC_128_44100_stereo.aax located in ~/Downloads/Audible/Audiobook/
    ```bash
    AAXtoMP3 -a -A <your_code> --use-audible-cli-data -t ~/Downloads ~/Downloads/Audible/Audiobook/Audiobook-LC_128_44100_stereo.aax
    ```
- **Convert Single Book (AAC, .aaxc):** No auth code needed.
  ```bash
  AAXtoMP3 -a --use-audible-cli-data -t <path_to_output_folder> <path_to_input_file.aaxc>
  ```
- **Convert Single Book (MP3):** Converts to `.mp3`. **NOTE: 10-15% larger than AAC; prefer AAC for efficiency.**
  ```bash
  AAXtoMP3 -s -A <your_code> --use-audible-cli-data -t <path_to_output_folder> <path_to_input_file>
  ```
- **Batch Convert (AAC, .aax, .aaxc):** Converts all `.aax`/`.aaxc` to `.m4a`.
  ```bash
  for f in <path_to_input_folder>/*.aax*; do AAXtoMP3 -a --use-audible-cli-data -t <path_to_output_folder> "$f"; done > ~/<path_to_log_folder>/conversion_log.txt 2>&1
  ```
  - Example: all audiobooks downloaded to ~/Downloads/Audible, converted to ~/Downloads/AAC, and logged to ~/Downloads
  ```bash
  for f in ~/Downloads/Audible/*.aax*; do AAXtoMP3 -a --use-audible-cli-data -t ~/Downloads/AAC "$f"; done > ~/Downloads/conversion_log.txt 2>&1
  ```
- **Debug Mode:** Verbose logs.
  ```bash
  AAXtoMP3 -a -A <your_code> --use-audible-cli-data -d -t <path_to_output_folder> <path_to_input_file>
