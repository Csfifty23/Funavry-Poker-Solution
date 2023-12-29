# Texas Hold'em Poker Image Processor

This notebook processes images from a Texas Hold'em Poker game and extracts player names and their corrosponding positions. The task was to use TrOCR for optical character recognition which only work on single line text and do not work on multiple lines. If there is an image in which text appers in more than one lines it will only recoginze the text from only one line. 

## Methodology

-The solution of the problem will only works if we can get only the detected portion in the images which only represent player name and their position.
-To effeicntly detect only the text sections corresonponding to the palyer name and palyer position i finetune the yolo8m model for the given images using ultralaytics becuase other methods and pretrained models 
-were not effeciently detecting the relevant text portion in images.
-Therefore i finetuned the yolo8m which is very fast and accurate and was giving the best results.
-After the fintuning infernce is done on the images and fintuned model was correctly detecting only the player name and palyer position in the images.
-The detected text boxes are then extracted out from the predicted images to perfom OCR using the TrOCR. 
-I used pretrained TrOCR for optical cahracter recogination from the huggingface liberary.
-Then a logic is written to mapped all the player name with their corrosponding position in a given input image.
-The script uses ultralatics to fintune the yolo8m model for detection of text boxes consists of player name and player position.
-TrOCR, an OCR tool, to extract text from single-line text images. 
-It processes the input image provided for testing the code ouput and extracts relevant information accordingly.

## Choices and Assumptions

- The script assumes that player names are at the start of the first line, and player positions are at the end of the second line on the player card.
- TrOCR is the only allowed OCR tool for this task.

## Dependencies

- All the dependencises are given in the requirements file.
- Also please follows these instruction to run the code successfully
- Please also keep in mind that you must need to restart the session after installing these dependencies otherwise you may face some nasty errors while runing the notebook.
- If you still face anykind please let me know.

## Files To Run The Notebook
To run this note book you need two files one is the file of yolo-finetuned model which can be download from the drive link. The other file is your image against which you want to evaulate the model. You have upload the for any of your text case and run the notebook with these two external files.

