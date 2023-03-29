# Importing-Data-in-Python
In this article, we explored how to import different types of data using various library. Such as pandas, csv, openpyxl, xlrd, json, Pillow, SkLearn, MoviePy and OpenCV.

![2019-12-how-to-import-data-into-python](https://user-images.githubusercontent.com/68110323/228432814-79397939-8005-49a2-9fec-e7175b45785e.jpg)

Python is a versatile programming language that is widely used for data analysis and scientific computing. One of the essential tasks in these domains is importing data into Python for processing and analysis. In this article, we will explore the various ways to import data into Python. Various types of data are as follows:

# 1. CSV files
CSV (Comma Separated Values) files are a common way of storing tabular data, and Python has a built-in module to handle them. The 'csv' module provides the functionality to read and write CSV files. To import a CSV file with csv library or pandas library, you can use the following code:

```
import csv

with open('file.csv', newline='') as csvfile:
    reader = csv.reader(csvfile)
    for i in range(5):
        row = next(reader)
        print(row)
import pandas as pd

file=pd.read_csv('file.csv')
file.head(5)
```

Here, we open the file 'filename.csv' in read mode and create a CSV reader object. We then use the list() function to convert the reader object into a list of lists, where each sublist represents a row in the CSV file.

# 2. Excel files
Excel files are another common way of storing tabular data. Python has several modules to handle Excel files, including pandas, openpyxl and xlrd. Here's how you can use the pandas, openpyxl and xlrdmodule to import first five rows of an Excel file:

```
import pandas as pd

file=pd.read_excel('file.xlsx')
file.head(5)
```
```
import openpyxl

workbook = openpyxl.load_workbook('file.xlsx')
worksheet = workbook.active

for i, row in enumerate(worksheet.iter_rows(values_only=True)):
    if i == 5:
        break
        
    for cell in row:
        print(cell, end='\t')
    
    print('\n')
```    
```    
import xlrd

workbook = xlrd.open_workbook('file.xls')
worksheet = workbook.sheet_by_index(0)

for i in range(min(5, worksheet.nrows)):
    row = worksheet.row_values(i)
    
    for cell in row:
        print(cell, end='\t')
    
    print('\n')
```
Here, we use the load_workbook() function to open the Excel file and the active property to select the active sheet. We then iterate over each row in the sheet and append it to a list. Note: panda and openpyxl can intake xlsx files, & xlrd can intake xls file.

# 3. Text files
Text files are a simple way of storing data, and Python can easily read and write them. Here's how you can import a text file in Python:
```
with open('file.txt') as file:
    content = file.read()

print(content)
```
Here, we open the file 'filename.txt' in read mode and use the read() method to read the entire file as a string. We then split the string into lines using the splitlines() method and store it in a list.
# 4. JSON files
JSON (JavaScript Object Notation) is a lightweight data format that is widely used for exchanging data between web services and applications. Python has a built-in module called json that can handle JSON data. Here's how you can import a JSON file in Python:
```
import json

with open('file.json', 'r') as f:
    data = json.load(f)

data
```
Here, we open the file 'filename.json' in read mode and use the json.load() method to load the data from the file into a Python object.

# 5. Importing Image Data in Python:
There are several ways to import image data in Python, but the most commonly used modules are Pillow, SkLearn and OpenCV.

## a). Pillow:
Pillow is a Python Imaging Library that supports opening, manipulating, and saving many different image file formats. you can use the following code to import an image:

```from PIL import Image

image = Image.open('person1.jpg')    # Open an image file
image.show()                         # Show the imageHere, we use the Image.open() method to open an image file and store it in the image variable. We then use the show() method to display the image.
```
## b). OpenCV:
OpenCV is a popular computer vision library that provides various image and video processing functions. It supports many image file formats and provides fast image processing capabilities. You can use the following code to import an image:
import cv2

image = cv2.imread('person1.jpg')    # Load an image file
cv2.imshow('Image', image)           # Show the image

cv2.waitKey(0)
cv2.destroyAllWindows()
Here, we use the cv2.imread() method to load an image file and store it in the image variable. We then use the cv2.imshow() method to display the image and the cv2.waitKey() and cv2.destroyAllWindows() methods to handle user input and close the window.
c). Scikit-image
Scikit-image or skimage is a Python library for image processing and computer vision tasks. It provides various functions for image manipulation, transformation, and analysis. You can use the following code to import an image:
from skimage import io

image = io.imread('person1.jpg')    # Load an image file
io.imshow(image)                    # Show the image

io.show()Here, we use the io.imread() method to load an image file and store it in the image variable. We then use the io.imshow() and io.show() methods to display the image.
Skimage also provides several functions for image preprocessing, such as image resizing, color conversion, and filtering. 
6. Importing Video Data in Python:
Python provides several modules to import video data, including OpenCV, MoviePy, and PyAV.
a). OpenCV:
OpenCV provides many video processing functions, including capturing and playing video files. You can use the following code to import a video:
import cv2

cap = cv2.VideoCapture('2girl_video2.mp4')    # Open a video file
while cap.isOpened():                         # Read the video frames
    ret, frame = cap.read()
    if ret:
        cv2.imshow('Video', frame)            # Display the video frames
        if cv2.waitKey(25) & 0xFF == ord('q'):
            break
    else:
        break

cap.release()                                 # Release the resources
cv2.destroyAllWindows()Here, we use the cv2.VideoCapture() method to open a video file and store it in the cap variable. We then use a loop to read each video frame using the cap.read() method, display the frames using the cv2.imshow() method, and handle user input using the cv2.waitKey() method. We release the resources using the cap.release() and cv2.destroyAllWindows() methods.
Conclusion:
In conclusion, importing data in Python is a critical task in data analysis and scientific computing. Python provides several modules to handle different types of data formats. Python provides several modules and libraries for importing and processing image and video data as well.
