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

