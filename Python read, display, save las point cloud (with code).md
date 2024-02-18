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
