# OCR On Texas Hold'em Poker Image 

This notebook processes images from a Texas Hold'em Poker game and extracts player names and their corrosponding positions. The task was to use TrOCR for optical character recognition which only work on single line text and do not work on multiple lines. If there is an image in which text appers in more than one lines it will only recoginze the text from only one line. 

## Methodology

- The solution of this problem will only works if we can get only the detected portion in the images which only represent player name and their position.
- To efficiently detect only the text sections corresonponding to the palyer name and palyer position i finetune the yolo8m model for the given images using ultralaytics becuase other methods and pretrained       
   models were not effeciently detecting the relevant text portion in images.
- Therefore i finetuned the yolov8 which is very fast and accurate and was giving the best results.
- ### Finetuning the Yolo8
    - To finetune the model on my poker images dataset i labal the images using roboflow.
    - After labeling the data we use ultralaytics and load the anotation file from the roboflow and Yolov8 to fintune the model.
    - After fintunig the model we export it using onnx.
    - This onnx save model is then used for detection of text boxes on test images 
- After the fintuning infernce is done on the images and fintuned model was correctly detecting only the player name and palyer position in the images.
- The detected text boxes are then extracted out from the predicted images to perfom OCR using the TrOCR. 
- I used pretrained TrOCR for optical cahracter recogination from the huggingface liberary.
- Then a logic is written to mapped all the player name with their corrosponding position in a given input image.
- The script uses ultralytics to fintune the yolov8 model for detection of text boxes consists of player name and player position.
- TrOCR, an OCR tool, to extract text from single-line text images. 
- It processes the input image provided for testing the code ouput and extracts relevant information accordingly.

## Choices and Assumptions

- No spcific assumptions are made

## Dependencies

- All the dependencises are given in the requirements file.
- Please also note that you may need to restart the session after installing these dependencies otherwise you may face some nasty errors while runing the notebook.
- If you still face anykind please let me know.

## Files To Run The Notebook
- To run this note book you need two files one is the file of yolo-finetuned model which can be download from the drive following drive link.
- [Download The Yolo Finetuned Model](https://drive.google.com/drive/folders/1DTx2lXzSr2x2q5kctTdAwAjp6rsyrnhB?usp=sharing)
- The other file is your image against which you want to evaulate the model. You need these two file for any of your text case and run the notebook with these two external files.

## Improvments 
- Althoug model is doing very well it may not produce the accurate palyer name and position accordingly.
- This is not because of the script logic but rahter due to detection model which is only finetuned on 42 images.
- This is because of time constraint and i could hardly label 42 images.
- Now its performance can be made perfect by finetuning on more images.
- The best part is now we have the pipeline in place and we can acheive the perfection by following the pipeline with more images.
