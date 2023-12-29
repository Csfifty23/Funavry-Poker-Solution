# Texas Hold'em Poker Image Processor

This notebook processes images from a Texas Hold'em Poker game and extracts player names and their corrosponding positions. The task was to use TrOCR for optical character recognition which only work on single line text and do not work on multiple lines. If there is an image in which text is appers two lines it will only recoginze the text from only one line. 

## Methodology

The script uses ultralatics to fintune the yolo8m model for detection of text boxes consists of player name and player position. TrOCR, an OCR tool, to extract text from single-line text images. It processes the input image provided through the `--image_path` argument and extracts relevant information.

## Choices and Assumptions

- The script assumes that player names are at the start of the first line, and player positions are at the end of the second line on the player card.
- TrOCR is the only allowed OCR tool for this task.

## Dependencies

- Python 3.x
- TrOCR (Reference: [TrOCR Documentation](link-to-TrOCR-docs))

## Installation

