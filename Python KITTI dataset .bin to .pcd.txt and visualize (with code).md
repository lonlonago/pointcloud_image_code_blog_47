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

