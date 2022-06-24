# EDU-SUM
______________________________________________________________
1. Origin 

Over the years the volume of video produced has seen a significant growth. Smartphones have made recording and uploading video content very convenient. Also the arrival of portable cameras and easy access to other recording devices, fast sharing of content, live recording of important events contributes a lot in the production of video data. CCTV cameras installed in almost every public place are another major source of video footage for security and surveillance purposes.
A large number of people record videos day and night producing a large volume of video data. Processing these video clips requires a lot of resources like human power, time and computer hardware storage etc. Video summarisation play an important role in tackling these issues. It helps with  fast browsing, proper storage and retrieving large amounts of video data without losing important features.

2. Summary of Requirement and Design 
* Scene detection done on the input videos. 
* Audio Extraction from each split of the video.
* Audio to Text conversion using speech recognition.
* Keyphrase extraction from the text output. 
* Summary in the form of slides and keyphrases along with corresponding video splits and full video. 

3. Proposed Methodology

Split the video in a manner so as to separate the subtopics taught in a lecture. 
Capturing the moment in the video as the professor switches the slide, we can say that the professor has moved on to the next subheading. 
We split the video wherever the change occurs. 
This helps us to capture the content of the blackboard as well in the image for summarisation
So our goal is to capture this change by using scene detection. 
Shot detection is done using “scoring”. In scoring each pair of consecutive frames of video is given a certain score which represent the similarity /dissimilarity between 2 different frames.
It helps in detecting the focus of the camera changes from professor to the slide, thus it detects changes in slides and changes in sub topics.
Thus the first step here is doing a shot detection which is done using opencv.
Generally slides are designed as images changes as the speaker speaks.
We just want the complete slides and no the incomplete slides.
So from each splitted video we extract the last image frame from a particular shot.
For video to audio conversion we have used the os and subprocess library of python. Looping over the directory of splitted videos to create audio file for each video split.
For audio to text conversion we have used a speech recognition library. Extracting the text from each audio file and saving in the .txt format.
Everything inside the text file may not be useful to be termed as keyword and cannot be represented in the summary.
From the text split file, we remove punctuations, special characters or stop words.
Now, we generate shingle files that contains 1,2 and 3 grams and their frequencies.
We consider a phrase as keyword if its frequency is more than one.
 
The images of slide show will be ordered.
They will be ordered in a sequence of extracted image from every splitted video.
The key phrase extractions would also be mapped to it accordingly.
Also, the original splitted video can be viewed whose last frame is visible as slide.
Keyword can be entered in the search bar, and all the slides containing that keyword can be viewed.
For searching, we loop through all the files inside the keyword split which contain all the keyphrases corresponding to each text split.
We remove all the commas inside keyphrase file using explode function which will store all comma separated strings into an array. Then we loop through that array.
If we come across the searched keyphrase inside the file, we load the corresponding slide file and display it on the website.
Here, the corresponding sequence and number of video split, text split, keyphrase split, frames matter the most to keep everything accurate.





