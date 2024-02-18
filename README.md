#  First, the principle of the algorithm 

   Pclpy supports the direct reading of the las format point cloud, but the RGB data format supported by pclpy is different from the RGB data format in the las point cloud, and needs to be converted. See the code for the conversion process. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574418690
  ```  
#  III. Display of results 

 ![avatar]( 1d201c68817d41029e280ffa58e3fc4b.png) 



--------------------------------------------------------------------------------

#  I. Overview 

   Pclpy is a Python implementation of the point cloud library PCL. The point cloud reading function that comes with pclpy does not support reading point clouds under the Chinese path. Pclpy contains laspy, so pclpy supports processing point clouds in las format. 

##  1. Read the point cloud 

 Mode 1: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574492833
  ```  
 Mode 2: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574492833
  ```  
##  2. Display point cloud 

   Python displays in many ways, and pclpy displays in a variety of ways. Here is just one of the simplest visualizations. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574492833
  ```  
##  3. Save the point cloud 

 Mode 1 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574492833
  ```  
 Mode 2 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574492833
  ```  
 The writer function has a total of 132 overloading methods, and those who are interested can open the PCDWriter.py to view. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574492833
  ```  
#  III. Display of results 

 ![avatar]( 8dcd237ee1404e5c9142971b270037da.png) 

#  IV. Relevant links 

 [1] WIN10系统下python快速安装点云库pclpy-0.11.0 

#  Test data 

 Open3D algorithm test data.rar 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Algorithm overview 

   Integral image is a method for performing normal estimation on ordered point clouds. The algorithm treats the point cloud as a depth image and creates certain rectangular regions on which the normals are calculated by taking into account the relationship between adjacent "pixels" (points) without running lookups on a search structure such as a KD tree. Therefore, its computational efficiency is very high, and the normals can usually be calculated in an instant. Therefore, it is best to use this method for real-time computation of ordered point clouds acquired from RGB-D sensors. Note: This method is only applicable to ordered point clouds!!! 

##  2. Main functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574455149
  ```  
 Set the normal estimation method. The algorithms currently implemented are: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574455149
  ```  
 Policies for setting processing boundaries. There are two strategies: BORDER_POLICY_IGNORE and BORDER_POLICY_MIRROR. 

##  3. References 

>  [1] doc:Normal Estimation Using Integral Images [2] PCL：pcl::IntegralImageNormalEstimation< PointInT, PointOutT >  [3] S. Holzer and R. B. Rusu and M. Dixon and S. Gedikli and N. Navab, Adaptive Neighborhood Selection for Real-Time Surface Normal Estimation from Organized Point Cloud Data Using Integral Images, IROS 2012. [4] D. Holz, S. Holzer, R. B. Rusu, and S. Behnke (2011, July). Real-Time Plane Segmentation using RGB-D Cameras. In Proceedings of the 15th RoboCup International Symposium, Istanbul, Turkey. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574455149
  ```  
#  III. Display of results 

 ![avatar]( 5eb0ae83caae40cca56e07d97516fca2.png) 

#  IV. Relevant links 

 [1] PCL 使用积分图进行法线估计 



--------------------------------------------------------------------------------

#  First, Las format analysis 

##  1. Public head 

   The common header is used to record the basic information of the dataset, such as the total number of Li-DAR points, the data range, the Li-DAR point format, the total number of variable-length records, etc. Since a LAS file may be directly generated from the data collected by the hardware or obtained after extracting, fusing, and modifying the existing data, the common header also records the generation method of the LAS file. For the characteristics of multiple returns of Li-DAR data, the common header also records the total number of Li-DAR points returned each time up to 5 returns. The common header also records the scale factor (scale) and offset value (offset) in the X, Y, and Z directions, which can reduce the length of each point record (Li-DAR point set records use the long type to record three-dimensional coordinates), and the true coordinates of Li-DAR point cloud data can be obtained by the following formula: where,, is the recorded value in the Li-DAR point cloud data. 

##  2. Variable length records 

   The variable-length record area is located after the public file header. The projection information, metadata information and user-defined information used to record data are the most flexible parts of the LAS format. Each variable-length record includes a fixed variable-length record head and a flexible extended domain. The length of a variable-length record = the length of the variable-length record head + the length of the extended domain. It contains some metadata, such as the coordinate system information of the point cloud data, the record label used to determine the starting position of each variable-length record, and the user ID of the variable-length record and the record ID determined by the LAS format. The point set record part saves a large amount of Li-DAR pin point information, which is the core of the LAS file, and records the three-dimensional coordinates and related attributes of each discrete point cloud. There are 100 Li-DAR point record formats supported by LAS, from Format 0 to Format 99. In the same LAS file, there is only one Li-DAR point format. And it must be consistent with the point format in the common header. Format 0 is the basic Li-DAR point record format, and other point formats are extended on the basis of Format 0. For example, the commonly used Format 1 format adds an attribute on the basis of Format 0 to record the GPS time of each pin point. This ensures the flexibility and extensibility of attribute records in the Li-DAR point format. The point record in Format 0 format contains a number of basic properties, such as spatial X, Y, Z coordinates, laser reflection intensity value, classification number of the current point, total number of echoes of the current laser pulse, the current pin point belongs to the first return, etc. Considering the characteristics of Li-DAR scanning by strip, the point record in Format 0 also includes information such as the current laser scanning angle and whether the current point is a strip edge point (the recording of this information helps to match and splice data between strips in subsequent processing). At present, LasiLib has been updated to LAS version 2.0.+, and LAS has gradually become an industry standard for Li-DAR data processing. 

##  3. References 

>  Sun Aiyi, Wang Jian. Analysis and conversion of LAS format [J]. Global Positioning System, 2016, 41 (02): 115-117 + 124. 

#  Install Laspy 2.0.2 

 PyPi pip install laspy 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428056
  ```  
 GitHub link: laspy 

#  III. Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428056
  ```  


--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

   See Open3D Radius Filter 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957446143
  ```  
#  III. Display of results 

##  1. Primitive point cloud 

 ![avatar]( aad0c027ef394c7abe8c9661e6a90246.png) 

##  2. The filtered point cloud 

 ![avatar]( 256bb0264e704933bff50c234438bffc.png) 



--------------------------------------------------------------------------------

#  Comparison of Several Point Cloud Registration Algorithms 

 Refer to many blogs, read a lot of algorithms for point cloud registration, decided to make a summary of point cloud registration these days, mainly to prevent yourself from forgetting. Mainly refer to the following blog, the link has been attached. https://blog.csdn.net/peach_blossom/article/details/78506184 

##  Algorithm implementation software and hardware environment 

 CPU：intel corei5-5200 @2.20Hz 

 sentire:Nvidia GeForce GTX 850M 

 Memory: 8GB 

 Operating System: Windows 10 Professional 

 Development environment: Vs2013 + pcl1.8.0 (release) 

 Point cloud registration dataset: bunny rabbits from different angles 

##  Second, point cloud registration comparison 

 2.1 Register the target. According to the original point cloud and the target point cloud, the transformation matrix, namely the rotation matrix R and the translation matrix T, is obtained by registration, and the error is calculated to compare the matching results. There are mainly the following comparisons: (1) based on local feature descriptors (PFH, FPFH, 3Dsc); (2) based on probability distribution (NDT); (3) ICP rough registration comparison. 

 2.2 Registration target (1) Extraction of key points (2) Feature description (3) Consistency estimation (4) Fine registration (5) Error analysis: There is a point cloud, and the target point cloud is obtained by continuously rotating the transformation. After that, the following registration methods are used to obtain R and T, and the actual transformation matrix is compared to obtain the error. 

 2.3 Comparison of rough registration, the principles of various algorithms for rough registration are not introduced, and many blogs have given detailed explanations. In registration, due to the characteristics of different point cloud datasets, different key points need to be extracted. This paper uniformly filters and samples the dataset to reduce the number of points to improve the efficiency of the algorithm. 

 ![avatar]( 20190305162728498.png) 

 2.3.1 result graph analysis, the original figure pfh rough registration fpfh rough registration 3Dsc rough registration ndt rough registration  

 2.3.2 time analysis 

 ![avatar]( 20190305163237134.png) 

 2.3.3 transformation matrix analysis, the transformation matrix structure is 

 ![avatar]( 20190305163651579.png) 

 ![avatar]( 20190305164331364.png) 

 2.3.4 error analysis  

 2.4 ICP usage in rough registration 

 ![avatar]( 20190305164512461.png) 

 ![avatar]( 20190305164524928.png) 

 ICP registration is generally used in fine registration. I read the online blog and it seems that it can be registered directly, so I registered two sets of point cloud datasets from different angles. The obtained results are as follows: t = 0.063s t = 0.05s 

 In ICP coarse registration, when given different data sets (point clouds with different R and T), ICP may fall into the local optimal solution, so ICP is generally used in fine registration, and good initial values need to be provided. 

 In summary, in the crude registration scheme, the time-consuming order of the algorithm is NDT < FPFH < PFH < 3Dsc; where the FPFH feature is the improvement of the PFH feature descriptor. NDT takes less time, but from the observation in the above figure, the initial value is not accurate enough. The rotation matrix R and translation matrix T are listed. 

 ![avatar]( 20190305164857512.png) 

 ![avatar]( 20190305164915739.png) 

 ![avatar]( 20190305164931643.png) 

 ![avatar]( 20190305164954129.png) 

 2.4 Complete registration comparison, the following several crude registration schemes, plus fine registration. Then compare the results. 2.4.1 the result diagram analysis pfh + icp fpfh + icp 3Dsc + icp ndt + icp 

 ![avatar]( 20190305165047499.png) 

 ![avatar]( 20190305165111748.png) 

 2.4.2 time analysis 2.4.3 transformation matrix analysis  

 ![avatar]( 20190305165139347.png) 

 2.4.4 error analysis, it can be concluded that the highest registration accuracy is 3Dsc, but it takes the longest. Time: ndt < fpfh < pfh < 3dsc 

 Code download link https://download.csdn.net/download/weixin_43236944/10997992 https://download.csdn.net/download/weixin_43236944/10998014 

 After the update in the next two months, PCL-based QT development will be completed 



--------------------------------------------------------------------------------

##  code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574471762
  ```  
##  III. Display of results 

 ![avatar]( 20210114171224866.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

 Open3D statistical filter 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574499664
  ```  
#  III. Display of results 

 ![avatar]( 6c15d54f649f42fe98ce99f6a8e95dd9.png) 

 Original point cloud, filtered point cloud  



--------------------------------------------------------------------------------

#  Using matlab to process point clouds 

 This paper mainly shares the use of MATLAB point cloud tools to deal with point clouds, and simple estimation and measurement of point cloud volume through point cloud contour. 

###  directory 

##  1. Main operation flow chart 

##  2. Specific process 

###  2.1 Point cloud reading and display 

 Suppose you have a point cloud file named pointcloud.ply - Introduction to the ply format 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574481502
  ```  
 Here it is important to note that the header file in the.ply file is formatted like this: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574481502
  ```  
 Where x, y, x are the spatial coordinates of the three-dimensional point cloud, followed by b, g, r represent the color of each point, the latter item is very important for texture mapping and display, can be extracted separately, and then displayed with pcshow; 

 Pcread generated after reading the file 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574481502
  ```  
 We can extract the position and color of it to texture map and paint 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574481502
  ```  
 ![avatar]( 20170823165248695) 

 Here is an example of using point cloud data generated by CMVS/PMVS methods:     

###  2.2 Processing of point clouds 

 In order to obtain the volume of this building, its volume is obtained by obtaining the contour envelope of this building. Mainly use the alphaShape function and volum in matlab 

 alphaShape This function is mainly used to extract edges from discrete 3D space point clouds and establish corresponding envelopes: shp = alphaShape (x, y, z) 

>  The main control parameters are alpha values, which are used to control the fineness of the production contour (the smaller the more delicate) 'RegionThreshold' ignores the small objects in the generated envelope, and presses the threshold volume of the small object'HoleThreshold 'to fill the holes in the envelope to generate a complete volume morph- * alphaShape (x, y, z, alpha,' HoleThreshold ', xx,' RegionThreshold ', xx) 

 It is important to note that the position coordinates of the point cloud need to be converted to a double-precision type. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574481502
  ```  
 ![avatar]( 20170823171754163) 

 The image above shows the generated point cloud envelope (requiring careful conditional parameters to generate an envelope that meets the required accuracy), and the approximate volume of this envelope can be calculated through volum. 



--------------------------------------------------------------------------------

#  First, the code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574426639
  ```  
#  III. Display of results 

   Take the conversion of the classical RPY Euler angle as an example and compare it with the results of the calculation tool. The following is the code calculation result: 

>  Euler angle to quaternion [[0.70710678 -0.70710678 0.] [0.70710678 0.70710678 0.] [0.0.1.] Euler angle to quaternion [0.0.0.38268343 0.92387953] 

 ![avatar]( 3dd04cb2e292409fa6c0e1a40ecc5417.png) 

 This is the calculation result of the calculation tool. It can be seen that the code is exactly the same as the rotation matrix calculated by the calculation tool; the output order of the quaternions in the code is: w, x, y, z (w is the imaginary part, x, y, z is the real part),



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

  Fabric simulation filtering process: 1) Use point cloud filtering algorithm or point cloud processing software to filter out abnormal points; 2) Invert the lidar point cloud; 3) Set the simulated fabric, set the mesh resolution of the fabric, and determine the number of simulated particles. The position of the fabric is set above the highest point of the point cloud; 4) Project the fabric simulation point and radar point to the horizontal plane, find the height value of the most adjacent laser point for each fabric simulation point, and set the height value to; 5) The fabric example is set to be movable, and the fabric particles are first affected by gravity. When the particle height is less than that, the particle height is set to; the particle is set to be immovable; 6) Calculate the internal force action between the fabric particles, and adjust the relative position between the fabric particles according to the set fabric rigidity parameters; 7) Repeat 5) and 6) calculations, and the number of iterations reaches the set maximum number of iterations; 8) Calculate the distance between the lidar point and the corresponding fabric simulation point. The distance is less than the threshold value and is marked as the ground point. The distance is greater than the threshold value Marked as a non-ground point. 

>  Introduction to "Cloth" Filtering Algorithm of Point Cloud Ground Point Filter (CSF) 

#  Second, read the las point cloud 

 Reference links: python reading las 1, GitHub: laspy 2, basic tutorial: Laspy: Documentation 3, installation: pip install laspy 4, use example: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957449665
  ```  
#  III. Algorithm source code 

 1. Algorithm details: CSF 2. Source code acquisition: https://github.com/jianboqi/CSF 3. Source code compilation: download the source code. In the python folder: python setup.py build python setup.py install 4. Read las and visualize the algorithm results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957449665
  ```  
#  IV. Display of results 

 ![avatar]( 20200906190452465.png) 

#  Implementation of CloudCompare 

 ![avatar]( 20200906191318615.png) 

 1. Load the point cloud data and click on the CSF Filter function in Plugins 2. The following window pops up: In the figure: Cloth resolution: refers to the mesh size of the cloth used to cover the terrain (in the same units as the point cloud). The larger the cloth resolution you set, the rougher the DTM you get; Max iterations: refers to the maximum number of iterations of the terrain simulation. 500 is enough for most scenarios. Classification threshold: refers to the threshold that divides the point cloud into ground and non-ground parts based on the distance between the point and the simulated terrain. 0.5 is suitable for most scenes. The minimum mesh resolution and distance threshold here can only be set to 10cm. The range of 10cm on the ground is the ground point by default, and the precision is not as high as in your own code implementation. 3. The final result: It can be seen that the curbs cannot be extracted from non-ground points. 



--------------------------------------------------------------------------------

#  First, the calculation process 

 ![avatar]( 20210307103542835.png) 

 1. According to the coordinate set of point cloud data, obtain the maximum and minimum values on the three coordinate axes. 2. Set the side length of the voxel small grid. 3. Find the side length of the minimum bounding box of the point cloud according to the maximum and minimum values on the three coordinate axes. 4. Calculate the size of the voxel grid.  

 6. Sort the elements in order from smallest to largest, calculate the center of gravity of each voxel small grid, and replace all points in the small grid with the center of gravity. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574472348
  ```  
#  III. Display of results 

 ![avatar]( 20200930211339729.png) 



--------------------------------------------------------------------------------

#  I. Overview 

 ![avatar]( 3fc17b29702a47ffab89b12666e7f2c4.png) 

   First of all, CloudCompare software should not support reading .bin data in KITTI data (anyway, the CloudCompare v 2.12 alpha I use is blind reading, how can a 1.8M file store more than a billion points?)  

   The main fields stored in the bin format point cloud in the kitti dataset are: x, y, z, and intensity. Open3D does not support the intensity field. Therefore, visualization of .bin to .pcd and .bin based on Open3D can only achieve format conversion display of x, y, and z coordinates. To realize the visualization of the x, y, z, and intensity field data in the bin format point cloud in the kitti dataset into .pcd and intensity information, you need to use pclpy. .bin to .txt has no restrictions, and any field information in .bin can be saved. 

#  二、Open3D 

##  1. Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428058
  ```  
##  2. Results display 

 ![avatar]( 334a29f5d689420bb4dc4cf8214617ef.png) 

#  Iii. pclpy 

##  1. Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428058
  ```  
##  2. Intensity display 

 ![avatar]( 66e432de10e04e0f88b3b62103931843.png) 

#  Fourth, .bin to .txt 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428058
  ```  
 ![avatar]( ff1c3fdc6ae84df589fb804dcef62a9a.png) 

 Convert to txt and read successfully   



--------------------------------------------------------------------------------

#  I. Overview 

   This article is a supplement to the content of Open3D Kmeans Point Cloud Clustering (Python Detailed Process Edition), with the following differences: 

 For the algorithm principle and detailed implementation process of Kmean clustering algorithm for point cloud processing, see: Open3D Kmeans point cloud clustering (python detailed process version) 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574468978
  ```  
#  III. Display of results 

##  1. Visualize the clustering results 

 ![avatar]( 8f7b08ac994449d9a390c55e0a6abf45.png) 

##  2. Save the point cloud clustering results 

 ![avatar]( 571158822c5b4612811f44d24cd39662.png) 



--------------------------------------------------------------------------------

#  1. Install laspy 2.0.2 

 PyPi pip install laspy 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
 GitHub link: laspy 

#  2. Laspy reading point cloud 

##  2.1 Read the entire content 

   The laspy.read () function in laspy reads everything in the file (public headers, variable-length records, dot records,...) and returns an object that can be used to access the data. Function parsing: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
 Code example: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
##  2.2 Reading part of the content 

   The laspy.open () function in laspy implements reading the common header and variable length records in the file. Function analysis: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
 The function opens the LAS/LAZ file in one of three supported modes: 

 Code example: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
##  2.3 Block reading 

   Sometimes files are too large to be fully read into RAM. LasReader can also do block-by-block read points on large files by using LasReader.chunk_iterator (), which is the object returned by the laspy.open () function, code example: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
#  3. Laspy save point cloud 

##  3.1 Direct storage 

   The laspy.write () function implementation in laspy saves the point cloud in .las or .laz format. Code example: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
##  3.2 Save in blocks 

   Like LasReader, there is a method for writing files block by block. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
#  4. Create a new las 

   Using las.create () or the LasData constructor of LasHeader, you can create a new las file from the public header. Public headers can be obtained from the file, or you can create new public headers yourself. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
#  5. Conversion of different versions of las 

   Laspy also provides the laspy.convert () function, which enables the ability to convert files between different versions and available point formats (as long as they are compatible). 

#  6. Information access 

##  6.1 Access to public headers 

   Access the public header of a read or opened las file by retrieving the header property: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
##  6.2 Access Point Records 

 To access point records using dimension names, there are two options: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
##  6.3 Accessing variable-length records 

   The size available in the file is determined by the point format id. The table in the introduction section contains a list of dimensions for each point format. To get the point format of the file, you must access it through the las object: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
   If you don't want to remember the latitude names for each dot format, you can use the following code to access the list of latitude names available in the file 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  
 This will provide you with all dimension names, including extra dimensions (if any). If you only want extra dimension names, you can get them using the following code: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428317
  ```  


--------------------------------------------------------------------------------

#  First, theoretical knowledge 

##  1. Principal curvature, mean curvature, and Gaussian curvature 

   Curvature is a measure of the degree of curvature of a curve. As an "external" bending measurement standard in differential geometry, the average curvature describes the curvature of a curved surface embedded in the surrounding space (such as a two-dimensional curved surface embedded in a three-dimensional Euclidean space). Gaussian curvature is a quantity that describes the concave-convex properties of a surface. When the degree of change of this quantity is large, the internal change of the surface surface is relatively large, which indicates that the smoothness of the surface is lower. There is a point cloud in the neighborhood of a surface approaching the point at any point in the point cloud, and the curvature at a point can be characterized by the local curvature of the surface fitted to the point and its neighborhood points. By least squares fitting, the quadric surface can be used to characterize the local area, and the principal curvature, average curvature, and Gaussian curvature at each point are calculated. 

##  2. Calculation of curvature 

   Take a data point in the scattered point cloud, and then take a point uniformly in the point cloud as the center. This point should cover the entire point cloud as much as possible. Through this point, the least squares method is used to fit the quadric surface. After solving the coefficients, the Gaussian curvature and average curvature of the data points are calculated according to the properties of the space surface curve. For the neighborhood of any data point in the measurement point cloud, the following formula needs to be minimized according to the principle of least squares; where the formula is a point in the field. The formula (1) is derived from the coefficients respectively, making them 0, and the following formula is obtained: From this, the quadric coefficient is solved. The curve equation is written in the form of a surface parameter equation: if there is a curve on the surface, the expression is: if the arc length of the curve is expressed by the compound function derivation formula, the arc length differential formula can be obtained: from the first basic formula of the surface can be obtained: If it is a point on the curve, use and to represent the unit tangent vector and the unit normal vector of the point, respectively. 

  By processing the two base roots of the variable, we can obtain Gaussian curvature according to the curvature property  

   mean curvature  

##  3. Type of local surface 

   According to the properties of differential geometry, the principal curvature is the embodiment of the local properties of the sampling point. Gaussian curvature is the product of the principal curvature. According to its sign, the properties of the point on the surface can be determined, indicating that the point is an ellipse point, a parabolic point, then, a hyperbolic point (K < O); the average curvature is the average value of the sum of the principal curvatures, which can indicate the convex and concave of the surface. Table 1 gives the average curvature and Gaussian curvature represented by different symbols. It can be seen from the table that the convex and concave information of the sampling point can be obtained from the symbol of the average curvature value. For sharp points with intense surface changes, there is no need to consider their specific convex and concave information when detecting. 

#  Code implementation 

 Currently only calculations for analog data are implemented 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574413388
  ```  
#  III. Display of results 

 ![avatar]( 20210513081854554.png) 

 ![avatar]( 20210513081846846.png) 



--------------------------------------------------------------------------------

#  First, read the point cloud 

   The laspy.read () function in laspy reads everything in the file (public headers, variable-length records, dot records,...) and returns an object that can be used to access the data.  

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574425481
  ```  
#  Second, show the true color point cloud 

   There is no function directly used for display in laspy. You can call the open3d library to visualize the point cloud. See Open3D to read, save, and display the point cloud. Among them, the code for true color display is as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574425481
  ```  
 ![avatar]( d44370df276b4620b35ad60987af3f3b.png) 

#  Rendering according to XYZ coordinates 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574425481
  ```  
 ![avatar]( d89d69a835aa4006acb04dfb220a118d.png) 

#  IV. Save the point cloud 

   The laspy.write () function implementation in laspy saves the point cloud in .las or .laz format. Code example: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574425481
  ```  


--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

>  The vtkMassProperties class can calculate the surface area and volume of triangular meshes, but the mesh must be closed triangular mesh data. For non-triangular meshes, the mesh needs to be converted to triangular mesh data. vtkTriangleFilter can convert polygonal mesh data to triangular mesh data. The use of this class is very simple, just set the vtkPolyData mesh data that needs to be converted as input. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574471339
  ```  
#  III. Display of results 

 ![avatar]( d120b92d6fc14ec5a6c7d14c023e278e.png) 

#  CloudCompare 

 ![avatar]( 2020122909411588.gif) 

 Implementation in CloudCompare software  

#  V. Experimental data 

 Link: https://pan.baidu.com/s/1mLe5X6YCsxwdHrZ6Ua8qzA Extraction code: h74h 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Implementation process 

   If the target point set corresponds to the reference point set, the corresponding points are satisfied: the number of points in the two point sets is equal, and the points in the point sets should correspond one-to-one. Let the rotation transformation vector be a unit quaternion: the rotation matrix can be obtained. Let the translation transformation vector be: the complete coordinate transformation vector can be obtained. Then the problem of finding the best coordinate transformation vector between the corresponding point sets can be transformed into the problem of getting a function: minimization. In the unit quaternion method, at least 3 pairs of coordinates of one-to-one corresponding points need to be known. The algorithm process is as follows: 1. Find the center of gravity respectively. The center of gravity of the original point is: After the conversion, the center of gravity of the point is: where, there is a pair of corresponding points, which 2. The constructed covariance matrix is: 3. The constructed matrix is: where, is the trace of the matrix; is, the identity matrix; is: where,. 4. Calculate the eigenvalue and eigenvector of the matrix, where the eigenvector corresponding to the largest eigenvalue is the unit quaternion. 5. Calculate the rotation matrix as: where, 6. Calculate the translation matrix as:  

##  2. References 

 [1]滕志远,张爱武.单位四元素法在激光点云坐标转换中的应用[J].测绘通报,2010(11):7-10.  

##  3. Main functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574471051
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574471051
  ```  
 Argmin () gets the subscript of the minimum value, using the same method as argmax (). 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574471051
  ```  
#  III. Display of results 

 ![avatar]( 88f6044deee446efb814849cfa5c43f0.png) 

 Initial position, position after registration  

#  IV. Test data 

 The test data is generated by MATLAB code, which is as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574471051
  ```  
#  V. Reference links 

 [1] Open3D 四元数、欧拉角、旋转向量转旋转矩阵 



--------------------------------------------------------------------------------

#  1. Fitting method 

#  2. Fitting the model 

 Module sample_consensus 

#  3. Implementation method 

 There are two implementations, and you need to pay attention to the use of the following code. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574446117
  ```  


--------------------------------------------------------------------------------

