# OCR On Texas Hold'em Poker Image 

This notebook processes images from a Texas Hold'em Poker game and extracts player names and their corrosponding positions. The task was to use TrOCR for optical character recognition which only work on single line text and do not work on multiple lines. If there is an image in which text appers in more than one lines it will only recoginze the text from only one line. To tackle this problem accuratly i had to perform the detection after finetunig the YOLOv8 model and extracted the detected text box. Now each detected text box can individiualy be given to the TrOCR for text recogintion inside the detected box. Also only those detected boxes will be recoginized which have confidence above 0.7. Lastely the I sorted the both the lists of saved player names boxes and player position boxes so that i accuratly mappped them palyer name with their corrosponding player position otherwise they will be randomly mapped the palyer name and player position which is not an accurate ouput that we want.

## Methodology

- The solution of this problem will only works if we can get only the detected portion in the images which only represent player name and their position.
- To efficiently detect only the text sections corresonponding to the palyer name and palyer position i finetune the YOLOv8 model for the given images using ultralaytics becuase other methods and pretrained       
   models were not effeciently detecting the relevant text portion in images.
- Therefore i finetuned the  YOLOv8 which is very fast and accurate and was giving the best results.
- ### Finetuning the Yolov8
    - To finetune the model on my poker images dataset i labal the images using roboflow.
    - After labeling the data i used ultralaytics and load the anotation file from the roboflow and Yolov8 to fintune the model.
    - After fintunig the model I exported it using onnx.
    - This onnx save model is then used for detection of text boxes on test images to palyer name and player position. 
- After the fintuning infernce is done on the images and fintuned model was correctly detecting only the player name and palyer position in the images.
- The detected text boxes are then extracted out from the predicted images to perfom OCR using the TrOCR which is an OCR tool, to extract text from single-line text images.
- The script uses ultralytics to fintune the yolov8 model for detection of text boxes consists of player name and player position. 
- I used pretrained TrOCR for optical cahracter recogination from the huggingface transformers liberary.
- Then a logic is written to mapped all the player name with their corrosponding position in a given input image.
- This logic can mapped the palyer name with their corrosponding position instead of randomply mapping the player name and player position which was required in this task.
- Also this logic can easily be modified if the player postion and player name change their position from the start of first line and end of second line respectively. For examples if player position comes at the the start of first line and palyer name at end of second line then this code can easily handle with a little change on the way i accessed the stored palyer name and player postion from their corrosponding lists. 


## Choices and Assumptions

- No spcific assumptions are made

## Dependencies

- All the dependencises are given in the requirements file.
- Please also note that you may need to restart the session after installing these dependencies otherwise you may face some nasty errors while runing the notebook.
- If you still face anykind please let me know.

## Files To Run The Notebook
- To run this note book you need two files one is the file of yolo-finetuned model which can be availble from the drive or can be download from the drive using following drive link.
- [Download The Yolo Finetuned Model](https://drive.google.com/drive/folders/1DTx2lXzSr2x2q5kctTdAwAjp6rsyrnhB?usp=sharing)
- The other file is your image against which you want to evaulate the model. You need these two file for any of your text case and run the notebook with these two external files.

## Improvments 
- Although model is doing very well it may not produce the accurate palyer name and position accordingly.
- This is not because of the script logic but rahter due to detection model which is only finetuned on 42 images.
- This is because of time constraint and i could hardly label 42 images.
- Now its performance can be made perfect by finetuning on more images.
- The best part is now we have the pipeline in place and we can acheive the perfection by following the pipeline with more images.
- Also the recogintion using TrOCR depends on the quality of the detection if detection is little odd then it also may not recoginized the text correctly and make stuff up and this is a commom problem in case of  
  language model. Overall the pipeline is the effective solution to the given problem and can easily be used to produce more accurate ouput with finetuning YOLOv8 over more images which i could not do becuase of time constraint required to anotate the data for finetuning YOLOv8 model. 
