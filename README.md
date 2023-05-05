Download Link: https://assignmentchef.com/product/solved-cv1-assignment-3
<br>
<h1>1             Circle detection</h1>

Figure 1 shows a selection of the last Finnish pre-euro coins (10, 5, and 1 marks; and 50 and 10 pennis, respectively). We apply the Hough transformation to detect the coins.

Figure 1: A selection of Finnish coins.

<ul>

 <li>Download the image jpg from Moodle. Read it and convert to grayscale.</li>

 <li>The mint specifies that the diameter of the 5 mark coin is 24.5 millimetres<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>. The resolution of the image is approximately 0.12 mm/pixel. Calculate the radius <em>r </em>of the coin in pixels. Apply the Canny edge detector to find edges in the grayscale image. Use the built-in function skimage.feature.canny. Visualize the edges and check that the outlines of the coins are detected.</li>

 <li>Use transform.hough circle to calculate the Hough transform of the edge detection result. Use the radius you calculated above. Draw the result. You should obtain something similar to Figure 2 that peaks strongly around the center of the 5 mark coin.</li>

 <li>Using transform.hough circle peaks, select the two highest peaks from the Hough transform. Get all outputs from the function, i.e., your call should look like: accums, cx, cy, radii = hough_circle_peaks(…).</li>

 <li>Apply patches.Circle to draw the circles at the coordinates found superimposed on the original image. See <a href="https://matplotlib.org/api/_as_gen/matplotlib.patches.Circle.html">https://matplotlib.org/api/_as_gen/matplotlib</a>. <a href="https://matplotlib.org/api/_as_gen/matplotlib.patches.Circle.html">patches.Circle.html</a> for more help. Use from matplotlib.patches import Circle to import the circle tool to your code.</li>

</ul>

Figure 2: Circle Hough transform result. The strongest peaks highlight the 5 mark coin centers (compare to Figure 1).

<h1>2             Fitting a line using RANSAC</h1>

Suppose you have some prior feature points extracted using some black box algorithm and they are stored in ”noisyedgepoints.npy” that you can download from Moodle. Those feature points represent a noisy version of an edge. Some of them are outliers and are not supposed to be part of the edge. Use the scikit library to fit the features such that you generate a best fitting line using RANSAC ( <a href="https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.RANSACRegressor.html">https://scikit-learn.org/stable/modules/generated/sklearn.linear_ </a><a href="https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.RANSACRegressor.html">model.RANSACRegressor.html</a><a href="https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.RANSACRegressor.html">)</a>. Alternatively, you may also implement your own version of RANSAC from scratch. The data file can be read as:

<table width="643">

 <tbody>

  <tr>

   <td width="37">with</td>

   <td width="605">open(‘noisyedgepoints.npy’, ‘rb’) as f: X = np.load(f) y = np.load(f)</td>

  </tr>

 </tbody>

</table>

1

2

3

After fitting the line, plot the outliers that got filtered by the RANSAC algorithm and the inliers respectively. The result should be similar to Figure 3.

Figure 3: Plot of results for task 2

<h1>3             Pen and paper task</h1>

This task expands on Question 2 of the ”Hough Transform and RANSAC” quiz:

<ul>

 <li>Suppose the fraction of outliers .</li>

 <li>The minimum number of samples to fit your model is <em>m</em>.</li>

 <li><em>k </em>is the number of running trials so that with probability <em>p</em>, at least one set of samples is free from outliers.</li>

</ul>

Prove that the number of trials is .

<a href="#_ftnref1" name="_ftn1">[1]</a> The diameters of the coins shown in Figure 1 from left to right are: 27.25mm, 24.5mm, 22.25mm, 19.7mm, and 16.3mm.