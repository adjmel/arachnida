# Image EXIF Extractor

This Python script extracts EXIF metadata (including details about the image format, mode, size, and any available EXIF tags) from one or more image files. It supports a variety of image formats including GIF, BMP, and more common formats like JPEG and PNG. 

The script also handles GIFs specifically by checking if they are animated and reporting the number of frames. If EXIF data is not available, the script will notify the user accordingly.

## Features
- Extracts EXIF data from images.
- Handles multiple image formats including GIF, BMP, PNG, and JPEG.
- Displays metadata such as image format, mode, size, EXIF tags, and if applicable, GIF animation details (e.g., number of frames).
- Gracefully handles errors such as missing files or images with no EXIF data.

## Requirements
- Python 3.x
- Required Python libraries:
    - **Pillow**: For image processing.
    - **Colorama**: For colored output in the terminal.
    - **argparse**: For command-line argument parsing.
  
### To install the necessary Python libraries, run:
```bash
pip install Pillow colorama
```

## Usage

### Basic usage
To analyze one or more image files and extract EXIF metadata, run the script from the command line with the following syntax:

```bash
python extract_exif.py <image_file_1> <image_file_2> ...
```

- Replace `<image_file_1>`, `<image_file_2>`, etc., with the file paths of the images you want to analyze.

For example:
```bash
python extract_exif.py image1.jpg image2.png image3.gif
```

### Script Output
The script will output the EXIF data or any relevant metadata for each image in a human-readable format. If an image has no EXIF data, a message indicating that will be displayed.

Sample Output:
```bash
Analyse du fichier : image1.jpg
Format: JPEG
Mode: RGB
Size: (1920, 1080)
...

Analyse du fichier : image2.png
Format: PNG
Mode: RGBA
Size: (800, 600)
Info: {'dpi': (300, 300)}
...
```

If the image is a GIF:
```bash
Analyse du fichier : animation.gif
Format: GIF
Mode: P
Size: (500, 300)
Is Animated: True
Frames: 10
...
```

## Error Handling
- If a file is not found, the script will return an error message: `Error: The specified file was not found.`
- If the image format is unsupported or there are other issues (e.g., missing EXIF data), the script will notify you with relevant information.

## Example

### Running the script on a single image:
```bash
$ python extract_exif.py my_image.jpg
```

Output:
```bash
Analyse du fichier : my_image.jpg
Format: JPEG
Mode: RGB
Size: (800, 600)
...
```

### Running the script on multiple images:
```bash
$ python extract_exif.py image1.jpg image2.png image3.gif
```

Output:
```bash
Analyse du fichier : image1.jpg
Format: JPEG
Mode: RGB
Size: (1920, 1080)
...

Analyse du fichier : image2.png
Format: PNG
Mode: RGBA
Size: (800, 600)
Info: {'dpi': (300, 300)}
...

Analyse du fichier : image3.gif
Format: GIF
Mode: P
Size: (500, 300)
Is Animated: True
Frames: 10
...
```

## Notes
- The script uses the **Pillow** library to handle image processing and **ExifTags** to extract EXIF metadata.
- For GIFs, the script checks if the image is animated and reports the number of frames.
- BMP and other image formats are also supported.
