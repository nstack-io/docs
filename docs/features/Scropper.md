---
currentMenu:  features-scropper
---

# Scropper

>#### Scropper has been removed and is no longer available in NStack!

(S)mart Cropper

New in 2.3.0

A feature to find a focal point in an image via machine learning. 
The focal point will indicate where in the image the important things are.

**Use cases:**

Auto crop image to many aspect ratios. Eg: in a CMS when saving new image

**Usages**

Scropper takes an image as input and outputs coordinates for the focal points baesd on high contrast, and a bounding box around any faces (if any) in the image. 

* Scropper only works with `.jpeg` or `.png` images for now.
* When sending a GET request with a URL to an image, the path must be directly to a readable image, e.g, this path `https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=934&q=80` won't  work, while this path `https://www.abc.net.au/news/image/8281460-3x2-700x467.jpg` will work. 
* The first call to Scropper will be slow (15-20s wait) while Lambda spins up. 
* Latency is a function of image size. Right now there are no limits. Expect approximately 1s latency for a 1MB image.

### Output

Scropper outputs two things:

1) The relative position of the focal point in the image represented by distance from top-left corner in percent on the x-axis and y-axis on the image. This will always be there.

2) A bounding box around faces. This will be empty if there are no detected faces in the image.

