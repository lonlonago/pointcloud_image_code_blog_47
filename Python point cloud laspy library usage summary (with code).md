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
