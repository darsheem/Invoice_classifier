# Invoice-classifier

This project uses openCV technology to read the invoice images, OCR technology to read text from images of invoices, intelligently (using NLP) classifies them under different categories like Food invoice, Electricity invoice, etc. and seaborn to visualize the category and its corresponding matches found in the text extracted from the image.

## Technologies used:
<ol>
  <li> Tesseract-OCR Tool </li>
  <li> Python 3.x </li>
  <ul>
    <li> opencv-python (cv2) </li>
    <li> pytesseract </li>
    <li> nltk </li>
    <li> re </li>
    <li> pillow (PIL) </li>
    <li> seaborn </li>
  </ul>
</ol>
Other modules like numpy,pandas,matplotlib,os and shutil are also used.

We need to download and install tesseract-ocr tool and set the path for the same.
We also need to install opencv-python(cv2), pytesseract,  pillow(PIL), seaborn.
pip install opencv-python
pip install pillow
pip install tesseract
pip install seaborn
pip install nltk
pip install pytesseract

## Working and execution of the system
<ol>
  <li> Once done with above steps of installation we will import all the necessary modules. </li>
  <li> We will set source path as the current working directory. </li>
  <li> We will get invoice image file name alongwith the path from the user. </li>
  <li> If input path exists we will check whether it is a directory or not. If it is a directory we will process all the image files inside it. </li>
  <ul>
    <li> Through get_img_text() function we will read image file using opencv module and through ocr (tesseract-ocr and pytesseract) we will extract the text from image. </li>
    <li> Through text_preprocessing() function we will replace all special symols by space using re (regular expression) module. Also we will convert the text extracted to lower case and split the text by space and lines. </li>
    <li> Through categorize_image() function we will check and determine the category (food, electricty, mobile, medicine, school) of each word by Stemming each word with nltk PorterStemmer.Also we will create a pandas dataframe with counts of the category as its data and index as the category (food, electricty, mobile, medicine, school) itself for visualizing it later using seaborn. </li>
    <li> Through save_output_copy() function based on the category of image determined by categorize_image() function we will print the category of the invoice image and also store the invoice image file to the folder of its corresponding category. </li>
    <li> Through visualize_prediction() function we will visualize each image using seaborn module. Here we will make use of the dataframe created in categorize_image() function and plot it using seaborn.barplot() function. For each image this will show the categories and the corresponding matches for each category found from the text extracted from that image. The category having maximum count will be said to be the category of that invoice image. </li>
    <li> Thorugh visualize_total_count() function we will visualize the total number of invoices for each category present in the directory given as input by the user. </li>
  </ul>
 <li> However, if the input path exists and is not a directory but an image file we will perform the above tasks for that particular image. </li>
</ol>
