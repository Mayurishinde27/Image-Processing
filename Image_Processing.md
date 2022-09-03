<div align = "center">
  <h1> Image Processing ⚡ </h1>
</div>

-----------------------



## > Why convert to grayscale?

- When loaded into memory, a grayscale image occupies a third of the space required for an RGB image.
- Because a grayscale image has a third of the data, it requires less computational power to process and can reduce computation time.
- A grayscale image is conceptually simpler than an RGB image, so developing an image processing algorithm can be more straightforward when working with grayscale.

----------------

## > Intensity Thresholding

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


## > [Automatic Thresholding](https://in.mathworks.com/help/images/ref/imbinarize.html)

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
 
 ## > Working With Binary Image
 
 - You can compute the sum across rows of an array using the sum function : <br>
```matlab
rSum = sum(BW,2)
```
- Plot the data : <br>
```matlab
plot(<data>)
```

 -----------------------------
 
 ## > Pre- and Postprocessing Techniques
 
 
 - Use the fspecial function to create an n-by-n averaging filter : <br>
 ```matlab
 
 F = fspecial("average",n)
 
 ```
 
 - Apply a filter F to an image I by using the imfilter function.
```matlab
Ifltr = imfilter(I,F);
```

- Structuring elements are created using the strel function.
```matlab
SE = strel("diamond",5)
 ```
 
 - To perform a closing operation on an image I with structuring element SE, use the imclose function.
```matlab
Iclosed = imclose(I,SE);

```

- In general, you can remove one image from another by subtracting it.
```matlab
Isub = I2 - I1;
```

- You can create a rectangular structuring element using strel with a size array in the format [height width].
```matlab
SE = strel("rectangle",[10 20]);
```

- To isolate the background, you wanted to eliminate the dark text by emphasizing the bright regions. To do this, you used imclose to close the image.

```matlab
Iclosed = imclose(I,SE);

```

- To emphasize the dark text instead, so you need to perform the opposite operation and open the image using imopen.

```matlab
Iopened = imopen(I,SE);
```
----------------------------------

 ### > Pre- and Postprocessing to Improve Segmentation
 
- Segmentation can be improved in two ways: by preprocessing the image before binarizing and by postprocessing the binary image itself.


1. Noise Removal
> Smooth pixel intensity values to reduce the impact of variation on binarization.

2.Background Isolation and Subtraction
> Isolate and remove the background of an image before binarizing.

3.Binary Morphology
> Emphasize particular patterns or shapes in a binary image.One way to remove text from an image is to use morphological operations.A morphological closing operation emphasizes the bright paper and removes the dark text.

4.Inverting a binary image
> A binary image is composed of 0s and 1s. In logical terms, 0 = false and 1 = true. The logical NOT operator (~) reverses the logical state (true becomes false and vice versa). You can use the ~ operator to invert a binary image, which changes all 1s to 0s, and vice versa.



