<div align = "center">
  <h1> Image Processing ⚡ </h1>
</div>

-----------------------



## Why convert to grayscale?

- When loaded into memory, a grayscale image occupies a third of the space required for an RGB image.
- Because a grayscale image has a third of the data, it requires less computational power to process and can reduce computation time.
- A grayscale image is conceptually simpler than an RGB image, so developing an image processing algorithm can be more straightforward when working with grayscale.

----------------

## Intensity Thresholding

- Show the image : <br>
```matlab
imshow(image_name)
```
- Plot the intensity histogram : <br>
```matlab
imhist(image_name)
 ```
- Logical operators to threshold the intensity values of a grayscale image, creating a binary image : <br>
```matlab
B = g > thresh;
 ```


## [Automatic Thresholding](https://in.mathworks.com/help/images/ref/imbinarize.html)

- To automate the threshold selection process, you can use the imbinarize function, which calculates the "best" threshold for the image : <br>
```matlab
 gBinary = imbinarize(g);
 ```
- You can have imbinarize look at smaller portions of the image and pick the best threshold for that region by passing the `adaptive` option as the second argument to imbinarize:<br>
```matlab
 gBinary = imbinarize(g,"adaptive");
  ```
- To display images in pair : <br>
```matlab
imshowpair(image1,imagw2,"Montage")
 ```
- In imbinarize, you can designate whether the foreground is bright or dark by setting the `ForegroundPolarity` option : <br>
 ```matlab
gBinary = imbinarize(g,"adaptive",...
            "ForegroundPolarity","dark")
 ```
 
 -----------------------------
 
 ## Working With Binary Image
 
 - You can compute the sum across rows of an array using the sum function : <br>
```matlab
rSum = sum(BW,2)
```
- Plot the data : <br>
```matlab
plot(<data>)
```
