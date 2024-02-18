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

