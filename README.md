# Texas Hold'em Poker Image Processor

This Python script processes images from a Texas Hold'em Poker game and extracts player names and positions.

## Methodology

The script uses TrOCR, an OCR tool, to extract text from single-line text images. It processes the input image provided through the `--image_path` argument and extracts relevant information.

## Choices and Assumptions

- The script assumes that player names are at the start of the first line, and player positions are at the end of the second line on the player card.
- TrOCR is the only allowed OCR tool for this task.

## Dependencies

- Python 3.x
- TrOCR (Reference: [TrOCR Documentation](link-to-TrOCR-docs))

## Installation

