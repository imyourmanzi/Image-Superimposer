# Image Superimoposer for CreateML

A tool to generate superimposed images randomly from a subject and background to feed into Apple's CreateML machine learning application.  This tool creates the image folder with annotations in the format that CreateML expects.

This tool is built with [Pillow](https://pypi.org/project/Pillow/) and supports its file [formats](https://pillow.readthedocs.io/en/stable/handbook/image-file-formats.html).  By default, the composite image format is saved in format detected from the background image at the time.  This setting, and others, can changed via command line options listed [below](#usage).

## Setup

Mirror the following for correct setup.  Items in `[brackets]` do not need to be created manually and may be overwritten.

### Directory Structure
```
Image-Superimoposer
├── README.md
├── image_create.py
├── img
│   ├── background
│   │   └── ...
│   ├── [generated]
│   │   ├── [annotations.json]
│   │   └── ...
│   └── subject
│       └── ...
└── requirements.txt
```

### Install
1. Setup your virtual environment (optional).
2. Install requirements with `pip`:
```shell
python3 -m pip install -r requirements.txt
```

## Usage

Ensure the that the script is executable with:
```shell
chmod u+x image_create.py
```

### Command Line Options

```
./image_create.py [-h]
                  [--color-temp {1000,1500,2000,2500,3000,3500,4000,4500,5000,5500,6000,6500,7000,7500,8000,8500,9000,9500,10000}]
                  [-f OUTPUT_FMT] [--inset-bottom INSET_BOTTOM]
                  [--inset-left INSET_LEFT] [--inset-right INSET_RIGHT]
                  [--inset-top INSET_TOP] [-n VARIATIONS] [--no-scale] [-q] [-v]
                  label

Generates composite photos for CreateML object recognition from subject and
background images.

positional arguments:
  label                 the name of the label for the subject's annotation

optional arguments:
  -h, --help            show this help message and exit
  --color-temp {1000,1500,2000,2500,3000,3500,4000,4500,5000,5500,6000,6500,7000,7500,8000,8500,9000,9500,10000}
                        the color temperature to convert all images to
  -f OUTPUT_FMT, --output-fmt OUTPUT_FMT
                        a string representing the Pillow library format to
                        save the generated composite image as
  --inset-bottom INSET_BOTTOM
                        percentage of the subject image's height to exclude in
                        the annotation from the bottom of the image (range:
                        1–99%)
  --inset-left INSET_LEFT
                        percentage of the subject image's width to exclude in
                        the annotation from the left of the image (range:
                        1–99%)
  --inset-right INSET_RIGHT
                        percentage of the subject image's width to exclude in
                        the annotation from the right of the image (range:
                        1–99%)
  --inset-top INSET_TOP
                        percentage of the subject image's height to exclude in
                        the annotation from the top of the image (range:
                        1–99%)
  -n VARIATIONS, --variations VARIATIONS
                        the number of variations to make with each image and
                        background pair
  --no-scale            do not change the scale of the subject image
                        (unexepected behavior for subject image larger than
                        background image)
  -q, --quiet           decrease the verbosity of log output (--verbose takes
                        precedence)
  -v, --verbose         increase the verbosity of log output (takes precedence
                        over --quiet)
```
