Green-Screen-Program-
=====================

from images import *

Puts a new background behind a photo

def replaceWall(originalImage, replaceImage):
        #I made a copy of the original image so that the changes don't permantly 
        # change the original
    copy = originalImage.copy() 
    height = copy.getHeight() 
    width = copy.getWidth()
    # This for loop goes through and finds the pixel colors
    for col in range(width): 
        for row in range (height):
            pixelColor = copy.getPixel(col, row)
            pixelRed = pixelColor[0]
            pixelGreen = pixelColor [1]
            pixelBlue = pixelColor [2]
            if pixelRed >= 100 and pixelGreen >= 100 and \
            abs(pixelRed-pixelGreen) <= 30 \
            and abs (pixelRed-pixelBlue) <= 30 \
            and abs (pixelGreen-pixelBlue)<= 30:
                newColor = replaceImage.getPixel(col, row)
                copy.setPixel(col, row, newColor)
                
    return copy 
    
def main(): 
    originalImage = FileImage('amy.gif')
    replaceImage = FileImage('background1.gif')
    newImage = replaceWall(originalImage, replaceImage)
    newImage.show()
    raw_input("press enter to quit")
main() 
