# ab_mover
Command line utility to read an Audiobookshelf metadata.json file and generate bash to create a directory structure based on it.

THIS DOES NOT ACUTALLY MOVE OR COPY FILES ITSELF. It is up to the user to look over the generated statements to make sure they are sane and aren't going to destroy their audiobbook library. 

Requirements: Python 3.10, Audiobookshelf, with the "Store metadata with item" enabled in settings.

---

## `ab_mover` Utility

### Overview
The `ab_mover` utility is a Python script designed to organize audiobook files into a structured directory format. The script processes audiobook metadata and moves or copies the files into a user-defined directory structure. It supports features like extracting book numbers from titles or series names, creating necessary directories, and handling various command-line options for flexibility.

### Features
- **Metadata Processing:** Reads metadata from `metadata.json` files to extract information such as title, author, and series.
- **Book Number Extraction:** Automatically extracts book numbers from directory names or series metadata.
- **Directory Organization:** Moves or copies files into a structured directory format based on author, series, and book number.
- **Command-Line Options:** Offers flexibility with options for copying files, enabling debug logs, and specifying a custom top-level directory.
- **Debug Logging:** Provides detailed logging for debugging purposes when enabled.

### Usage
```sh
./ab_mover <base_directory> [-c] [--debug] [-t <top_level_directory>]
```

### Command-Line Arguments
- `base_directory`: The base directory to search for audiobooks.
- `-c, --copy`: Copy files instead of moving them. By default, files are moved.
- `--debug`: Enable debug logging for detailed information about the script's operations.
- `-t, --top-level-dir`: Specify a custom top-level directory for audiobooks. The default is `/Audiobooks`.

### How It Works
1. **Walking Through Directories:** The script recursively walks through the specified base directory to locate `metadata.json` files.
2. **Processing Metadata:** For each `metadata.json` file found, the script extracts the title, authors, series, and potentially the book number.
3. **Directory Creation:** Based on the extracted metadata, the script constructs a target directory path in the form of `<top_level_directory>/<author>/<series>/Book <book_number>`.
4. **File Movement/Copying:** The script generates and prints bash commands to move or copy the files from the source to the target directories, depending on the specified options.
---
