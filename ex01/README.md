# Image Downloader - README

## Description

The **Image Downloader** script is a Python-based tool designed to download images from a specified URL. It allows for both single-page and recursive downloads, where you can define the maximum depth for the recursive crawl. The downloaded images are saved to a local directory, with the option to specify a custom location.

The script uses the following Python libraries:
- `requests` for HTTP requests
- `BeautifulSoup` (from `bs4`) for HTML parsing
- `colorama` for adding color output to the terminal
- `argparse` for handling command-line arguments

## Features

- **Download Images**: Extract and download images from a webpage.
- **Recursive Download**: Crawl through pages linked from the initial URL and download images from those as well.
- **Control Maximum Depth**: Define the maximum depth for the recursive download (default is 5).
- **Custom Save Path**: Specify the path where images will be saved. By default, images are saved in `./data/`.

## Prerequisites

- Python 3.x
- Required Python libraries: `requests`, `beautifulsoup4`, `colorama`

### To install the required libraries, use the following command:

```bash
pip install requests beautifulsoup4 colorama
```

## Usage

The script can be executed from the command line, and it requires at least one argument: the URL from which to download images.

### Basic Usage

```bash
python image_downloader.py <URL>
```

Where `<URL>` is the URL of the website from which you want to download images. The images will be saved in the default directory `./data/`.

### Usage with Options

```bash
python image_downloader.py <URL> -p <path> -r -l <max_depth>
```

#### Arguments

- `-p <path>`: (Optional) Specify the path where images will be saved. Default is `./data/`.
- `<URL>`: (Required) The URL of the website from which to download images.
- `-r`: (Optional) If specified, the script will download images recursively, i.e., follow links in the HTML and download images from those pages as well.
- `-l <max_depth>`: (Optional) Set the maximum depth for recursive downloading (default is 5). If `-r` is specified, the script will crawl through pages up to this depth.

### Example

1. **Download images from a single page**:
   ```bash
   python image_downloader.py https://example.com
   ```

2. **Download images recursively with a maximum depth of 3**:
   ```bash
   python image_downloader.py https://example.com -r -l 3
   ```

3. **Download images and save them in a custom directory**:
   ```bash
   python image_downloader.py https://example.com -p ./images/
   ```

4. **Download images recursively with a custom depth and save them in a custom directory**:
   ```bash
   python image_downloader.py https://example.com -r -l 2 -p ./images/
   ```

## How it Works

1. **Requests**: The script sends HTTP requests to the provided URL and retrieves the HTML content.
2. **HTML Parsing**: It uses BeautifulSoup to parse the HTML and locate `<img>` tags to extract image URLs.
3. **Download and Save**: It downloads each image using the `requests` library and saves it to the specified directory.
4. **Recursive Download**: If the `-r` option is specified, the script follows links (`<a>` tags with `href` attributes) on the page and downloads images from the linked pages, up to the specified maximum depth.

## Handling Errors

- **Network Issues**: If the script encounters network problems or cannot download an image, it will display an error message and continue.
- **Unsupported Image Formats**: The script only supports downloading common image formats like JPG, PNG, GIF, and BMP. If an unsupported format is encountered, it will skip the image.
- **Keyboard Interrupt**: If the user interrupts the process (e.g., by pressing `Ctrl+C`), the script will exit gracefully.

## Example Output

```
The images will be uploaded to the directory : ./data/
URL : https://example.com
Maximum depth level of the recursive download : 3

Image 0 saved as ./data/image_1_0.jpg
Image 1 saved as ./data/image_1_1.png
...
Download complete ✅
```
