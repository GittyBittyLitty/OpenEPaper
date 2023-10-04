Due to the characteristics of e-paper technology, electronic tags can only display pure white, black, and red colors. To ensure legibility, certain considerations need to be taken into account when displaying text on these tags.

The file format for images to be displayed on e-paper tags is JPEG with the baseline (non-progressive) specification.
To ensure the image is displayed correctly without distortion, it is essential that the image dimensions precisely match the size of the tag screen: 152x152 pixels for 1.54", 296x128 pixels for 2.9", and 400x300 pixels for 4.2". The esp32 is not powerful enough to do image resize.

When incorporating text in images, avoid using anti-aliasing. Rendering fonts without anti-aliasing can be challenging for some libraries. A workaround is to start with an indexed colored image that uses a palette consisting of white, black, and red. By drawing the text on this indexed colored image and subsequently converting it to a 24-bit RGB image, you get rid of the antialiassing. An example demonstrating this technique can be found in the [[Push external image|Image-upload]] article.

When saving the image file, it is recommended to use the maximum or near maximum JPEG quality. This ensures that the image employs 4:4:4 quantization, which maintains sharp transitions between red and white without introducing artifacts. Lower quality JPEGs often use 4:2:0 quantization, which can result in undesirable artifacts and less crisp transitions between colors.

To do this in GIMP, under Export (as jpeg) open Advanced Options and uncheck Progressive and select 4:4:4 from Subsampling.

👎 Wrong image: text rendered on a 24 bit RGB image, saved as standard quality, 300% zoomed for demo:
![Wrong image](usage/output-wrong.jpg)

👍 Correct image: text rendered on a indexed color image, saves as maximum quality, 300% zoomed for demo:
![Correct image](usage/output-right.jpg)
