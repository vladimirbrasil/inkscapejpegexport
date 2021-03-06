# Inkscape JPEG Export Extension

This is a small and basic [http://inkscape.org Inkscape] extension that allows to export directly to a JPG file instead of the standard PNG. It is one of my first works in Python and is developed for my personal needs, so I will be glad if you find it useful, but I can't say if it will work for you too.

## How it works

This extension simply exports a PNG image and then converts it to JPEG using '''ImageMagick'''; this means that you must have ImageMagick installed to make it work.

The extension has three exporting modes:
* '''full page export''' exports the whole page;
* '''fast mode export''' uses Inkscape's simpletransfor library to determine area and position of the selected objects and exports them. This has some issues with masks and clips, and, in Inkscape versions prior to 0.49, with images. In any other case this is the recommended method since it is much, much faster than the one below;
* '''normal mode export''' calls a command line Inkscape instance for every selected object to get its data. This method doesn't have any problems with clips, masks and images but is much, much slower than the one above if you have many objects selected.

# Upgrade by Vla

If no export path is informed, it'll default to the Pictures folder (~/home/[user]/Pictures) with the same name of the svg file.

For now it is not configured to work with Windows. 

## Installation

Just drop the two jpegexport.* files in your extensions folder.

```
cd /usr/share/inkscape/extensions/
sudo cp [drag file here to know the full path and remove quotes].py jpegexport.py
sudo cp [drag file here to know the full path and remove quotes].inx jpegexport.inx
```

## Usage

The extension can be found in the Extensions menu > Export > JPEG Export.

### Options

* '''Export path''': write here the full path and file name of the resulting image.
* '''Background color''': Since JPEG does not support transparency, the image will have a background color. Default is white, if you want to change it insert in this field the desired color in CSS hexadecimal notation (e.g. #000000 for black).
* '''Export whole page''': check this if you want to export the whole page instead of a selection.
* '''Fast export''': use the fast or the normal export mode (see above for details). It is recommended to always check this box unless you are using masks or clips. This option has no effect if you are exporting the whole page.