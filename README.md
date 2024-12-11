# SSD1306 Bitmap Generator

A Python script to convert images into bitmaps suitable for SSD1306 OLED displays. The generated bitmap is in C array format and can be used directly in your Arduino or embedded projects.

## Features
- Converts images to monochrome bitmaps.
- Outputs the bitmap in a C array format.
- Configurable threshold for black-and-white conversion.

## Prerequisites
Make sure you have Python installed along with the following dependencies:

- [Pillow](https://python-pillow.org/) (Python Imaging Library fork)

Install Pillow using pip:
```bash
pip install pillow
```

## Usage

### Command-line Execution
```bash
python bitmap_generator.py <image_path> <output_file>
```
- `<image_path>`: Path to the input image file.
- `<output_file>`: Name of the output file where the bitmap will be saved.

### Interactive Mode
Run the script without arguments to provide inputs interactively:
```bash
python bitmap_generator.py
```
You will be prompted to:
- Enter the path to the image file.
- Enter the name of the output file.

## Output Format
The output is a C array in the following format:
```c
const uint8_t PROGMEM splash[] = {
    0b11000000, 0b11110000, // Example bitmap row
    0b01111000, 0b00011100, // Example bitmap row
    ...
};
```
- Each `0b` represents a byte in binary form.
- Rows are padded to ensure byte alignment.

## Example
### Input Image:
An image `example.png`.

### Command:
```bash
python bitmap_generator.py example.png output_bitmap.c
```

### Output (`output_bitmap.c`):
```c
const uint8_t PROGMEM splash[] = {
    0b11111111, 0b00000000,
    0b00000001, 0b11111110,
    0b00001111, 0b11111111,
    ...
};
```

## Additional Options
- **Threshold Adjustment**: Modify the `threshold` value in the `image_to_bitmap` function to control the black-and-white conversion. Default is `50`.

## Developer Information
- **Author**: Saurav Sajeev
- **Purpose**: Developed to simplify the process of generating bitmaps for SSD1306 OLED displays.

Feel free to contribute or report issues to improve this tool!

