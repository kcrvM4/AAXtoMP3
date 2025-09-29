# AAXtoMP3 Cheat Sheet

**Purpose:** Convert `.aax`/`.aaxc` to `.m4a`/`.mp3`/`.flac`/`.opus` with metadata/chapters. `.aax` requires auth code; `.aaxc` uses `.voucher`.

**Commands:**
- **Help:** Show all options.
  ```
  AAXtoMP3 -h
  ```
- **Convert Single Book (AAC, .aax):** Converts to `.m4a` with metadata/chapters.
  ```
  AAXtoMP3 -a -A <YOUR_CODE> --use-audible-cli-data -t <PATH_TO_OUTPUT_FOLDER> <PATH_TO_INPUT_FILE>.aax
  ```
  - Example: Audiobook-LC_128_44100_stereo.aax located in ~/Downloads/Audible/Audiobook/
    ```
    AAXtoMP3 -a -A <YOUR_CODE> --use-audible-cli-data -t ~/Downloads ~/Downloads/Audible/Audiobook/Audiobook-LC_128_44100_stereo.aax
    ```
- **Convert Single Book (AAC, .aaxc):** No auth code needed. `--use-audible-cli-data` flag is not needed since it is turned on by default for `.aaxc` files.
  ```
  AAXtoMP3 -a -t <PATH_TO_OUTPUT_FOLDER> <PATH_TO_INPUT_FILE>.aaxc
  ```
- **Convert Single Book (MP3):** Converts to `.mp3`. **NOTE: 20-30x slower conversion than AAC!**
  ```
  AAXtoMP3 -s -A <YOUR_CODE> --use-audible-cli-data -t <PATH_TO_OUTPUT_FOLDER> <PATH_TO_INPUT_FILE>
  ```
- **Batch Convert (AAC, .aax, .aaxc):** Converts all `.aax`/`.aaxc` to `.m4a` and writes to a text file for easy review after conversion.
  ```
  AAXtoMP3 -a --use-audible-cli-data -t <PATH_TO_OUTPUT_FOLDER> <PATH_TO_INPUT_FOLDER>/*.aaxc > <PATH_TO_LOG_FOLDER>/conversion_log.txt 2>&1
  ```
  - Example: all audiobooks downloaded to ~/Downloads/Input, converted to ~/Downloads/Output, and logged to ~/Downloads
    ```
    AAXtoMP3 -a --use-audible-cli-data -t ~/Downloads/Output ~/Downloads/Input/*.aaxc > ~/Downloads/conversion_log.txt 2>&1
    ```

    - **Note:** to monitor progress, open another terminal window and use `tail -f`:
      ```
      tail -f ~/Downloads/conversion_log.txt
      ```

- **Debug Mode:** Verbose logs.
  ```
  AAXtoMP3 -a -A <YOUR_CODE> --use-audible-cli-data -d -t <PATH_TO_OUTPUT_FOLDER> <PATH_TO_INPUT_FILE>
