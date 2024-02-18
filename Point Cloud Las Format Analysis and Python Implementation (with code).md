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
