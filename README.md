Download Link: https://assignmentchef.com/product/solved-cse527-homework1-a-gaussian-convolution
<br>



<strong>Problem 1.a Gaussian convolution :</strong> Write a function in Python that takes two arguments, a width parameter and a variance parameter, and returns a 2D array containing a Gaussian kernel of the desired dimension and variance. The peak of the Gaussian should be in the center of the array. Make sure to normalize the kernel such that the sum of all the elements in the array is 1. Use this function and the OpenCV’s filter2D routine to convolve the image and noisy image arrays with a 5 by 5 Gaussian kernel with sigma of 1. Repeat with a 11 by 11 Gaussian kernel with a sigma of 3. There will be four output images from this problem, namely, image convolved with 3×3, 11×11, noisy image convolved with 3×3, and 11×11. Once you fill in and run the codes, the outputs will be saved under Results folder. These images will be graded based on the difference with ground truth images. You might want to try the same thing on other images but it is not required. Include your notebook and the saved state where the output is displayed in the notebook.

<strong>Problem 1.b Median filter {15 pts}:</strong>  (a)Write a function to generate an image with salt and pepper noise. The function takes two arguments, the input image and the probability that a pixel location has salt-pepper noise. A simple implementation can be to select pixel locations with probability ‘p’ where noise occurs and then with equal probability set the pixel value at those location to be 0 or 255.(<strong>Hint: Use</strong>

<strong>np.random.uniform()</strong>)  (b)Write a function to implement a median filter. The function takes two arguments, an image and a window size(if window size is ‘k’, then a kxk window is used to determine the median pixel value at a location) and returns the output image. <strong>Do not</strong> use any inbuilt library (like scipy.ndimage_filter) to directly generate the result.  For this question display the outputs for “probabilty of salt and pepper noise” argument in the <strong>noisy_image_generator</strong> function equal to 0.1 and 0.2, and median filter window size in <strong>median_filter</strong> function equal to 5×5.  (c) What is the Gaussian filter size (and sigma) that achieves a similar level of noise removal.

similar level of noise removal as shown below. However, gaussian filter will not give similar denoising performance as median filter is doing in case of salt and pepper noise removal. Because to reduce noise intensity (lets say blur in case of gaussian), sigma should be increased and with higher sigma (standard deviation) high frequency details i.e. edges will get blurred.

<strong>Problem 2 Separable convolutions {15 pts}:</strong> The Gaussian kernel is separable, which means that convolution with a 2D Gaussian can be accomplished by convolving the image with two 1D Gaussians, one in the x direction and the other one in the y direction. Perform an 11×11 convolution with sigma = 3 from question 1 using this scheme. You can still use filter2D to convolve the images with each of the 1D kernels. Verify that you get the same results with what you did with 2D kernels by computing the difference image between the results from the two methods. This difference image should be close to black. Include your code and results in your colab Notebook file. There is no output image from this part. Be sure to display the result images in the notebook.

<strong>Problem 3 Laplacian of Gaussian {20 pts}:</strong> Convolve a 23 by 23 Gaussian of sigma = 3 with the discrete approximation to the Laplacian kernel [1 1 1; 1 -8 1; 1 1 1]. Plot the Gaussian kernel and 2D Laplacian of Gaussian using the Matplotlib function plot . Use the Matplotlib function plot_surface to generate a 3D plot of LoG. Do you see why this is referred to as the Mexican hat filter? Include your code and results in your Colab Notebook file. Apply the filter to the <strong>four output images generated in the previous question</strong>. Discuss the results in terms of edge accuracy and sensitivity to noise.

<strong>Discuss the results in terms of edge accuracy and sensitivity to noise.</strong>

-&gt; As laplacian filter (derivative filter) is very sensitive to noise, it is always advisable to smooth the image or lets say apply Gaussian filter before convolving with laplacian filter. Here it is visible that in first image which had noise initially is having small edges which are not meaningful or smaller compared to other important edges like face outlines. These unimportant edges are somewhere reducing the effect of the important edges because in the second image which had Gaussian filter applied in X direction, it is more clear to see the main edges of the human. Coming to the last two images, both were blurred (noise was reduced to make it less sensitive to noise) before applying laplacian, so they are able to show larger edges accurately but the smalled edges (such as lines in hat) are not accurate because of smoothing. Finally I can say that to keep it less sensitive we are losing smaller edges (like hair in first image) and if we care about smaller edges (not applying gaussian filter) it becomes very sensitive to noise.

<strong>Problem 4 Histogram equalization {20 pts}:</strong> Refer to Szeliski’s book on section 3.4.1, and within that section to eqn 3.9 for more information on histogram equalization. Getting the histogram of a grayscale image is incredibly easy with python. A histogram is a vector of numbers. Once you have the histogram, you can get the cumulative distribution function (CDF) from it. Then all you have left is to find the mapping from each value [0,255] to its adjusted value (just using the CDF basically). <strong>DO NOT</strong> use <strong>cv2.equalizeHist() </strong>directly to solve the exercise! We will expect to see in your code that you get the PDF and CDF, and that you manipulate the pixels directly (avoid a for loop, though). There will be one output image from this part which is the histogram equalized image. It will be compared against the ground truth.

<strong>Problem 5 Low and high pass filters {20 pts}:</strong> Start with the following tutorials:  <u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">http://docs.opencv.or</a></u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">g</a><u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">/master/de/dbc/tutorial_p</a></u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">y</a><u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">_fourier_transform.html (http://docs.opencv.or</a></u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">g</a><u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">/master/de/dbc/tutorial_p</a></u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">y</a><u><a href="http://docs.opencv.org/master/de/dbc/tutorial_py_fourier_transform.html">_fourier_transform.html) </a><a href="http://docs.opencv.org/2.4/doc/tutorials/core/discrete_fourier_transform/discrete_fourier_transform.html">http://docs.opencv.or</a></u><a href="http://docs.opencv.org/2.4/doc/tutorials/core/discrete_fourier_transform/discrete_fourier_transform.html">g</a><u><a href="http://docs.opencv.org/2.4/doc/tutorials/core/discrete_fourier_transform/discrete_fourier_transform.html">/2.4/doc/tutorials/core/discrete_fourier_transform/discrete_fourier_transform.html (http://docs.opencv.or</a></u><a href="http://docs.opencv.org/2.4/doc/tutorials/core/discrete_fourier_transform/discrete_fourier_transform.html">g</a><u><a href="http://docs.opencv.org/2.4/doc/tutorials/core/discrete_fourier_transform/discrete_fourier_transform.html">/2.4/doc/tutorials/core/discrete_fourier_transform/discrete_fourier_transform.html)</a></u> For your LPF (low pass filter), mask a 60×60 window of the center of the FT (Fourier Transform) image (the low frequencies). For the HPF, mask a 20×20 window excluding the center. The filtered low and high pass images will be the two outputs from this part and automatically saved to the Results folder.