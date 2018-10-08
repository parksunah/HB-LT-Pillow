
<br><br><br><br>
# An Intro to Pillow
Python Image Library
<br><br><br><br>
18/10/8 <br>
Hackbright Lightning Talk <br>
Sunah Park <br>
<br><br><br><br>


## Install Pillow

$ pip3 install pillow

## Opening Images


```python
from PIL import Image
```

The most important class in the Python Imaging Library is the Image class, defined in the module with the same name.<br>
To load an image from a file, use the open() function in the Image module.


```python
img = Image.open("melon.jpg")
```

Once you have an instance of the Image class, you can use the methods defined by this class to process and manipulate the image.<br> Let’s display the image we just loaded.


```python
img.show()
```

## Getting Image Information

Instances of the Image class have the following attributes.


```python
print(img.size)
```

    (1000, 667)



```python
print(img.format)
```

    JPEG


## Editing Images

### Cropping

`Image.crop((left, upper, right, lower))`


```python
cropped_img = img.crop((0, 80, 500, 400))
cropped_img.show()
```

### Rotating

`Image.rotate(angle)`


```python
rotated_img = img.rotate(90)
rotated_img.show()
```

### Saving


```python
rotated_img.save("rotated_melon.jpg")
```

### Split and Merge

`Image.split()`

`Image.merge(mode, bands)`

- Parameters :	<br>
mode –  The type and depth of a pixel in the image. (e.g., RGB) <br>
bands – A sequence containing one single-band image for each band in the output image. (e.g., RGB has r, g, b)


```python
r, g, b = img.split()
new_img = Image.merge("RGB", (b, g, r))
new_img.show()
```

### Black and White - create a simple function

`Image.convert(mode)`

- Parameter : mode – The requested mode. (e.g., Black and White - L, RGB, etc.)


```python
def black_and_white(input_image_path, output_image_path):
    """ Saving an image as Black and White """
    
    color_image = Image.open(input_image_path)
    bw = color_image.convert('L')
    bw.save(output_image_path)
```


```python
black_and_white('melon.jpg', 'bw_melon.jpg')
```

## Using Filters

The ImageFilter module contains definitions for a pre-defined set of filters, which can be be used with the Image.filter() method.


```python
from PIL import ImageFilter
```


```python
blur_img = im.filter(ImageFilter.BLUR)
blur_img.show()
```

<br><br>
# Reference <br>
https://pillow.readthedocs.io/en/5.3.x/index.html <br>
https://www.blog.pythonlibrary.org/?s=pillow <br><br>


