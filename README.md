# Pic-2-Tic

A web-app designed specifically to convert images for use with the TIC-80 fantasy console. The project is still a work in progress (WIP), but once it's finished, a standalone version will be packaged, perhaps with Electron or NW.js.

For now, you can run the app by using VS Code and the [Live Server plugin](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer). More experienced users feel free to run/host the files however you see fit. Please note that I am not an experienced web developer, and the code could definitely be refactored. I only made this tool for a personal need I have developing 'Craptorio' a factorio de-make for the tic80, however it occured to me that this could be useful to other tic80 devs. I welcome any criticism/input/pull requests, so feel free to contribute if so inclined.

![image](https://user-images.githubusercontent.com/25288625/227027839-fca3cd29-7825-4be3-9474-2f851ca1612d.png)

## Features
- Load any image and convert it's colors to the selected palette (using closest color algorithm)
- Two images displayed: the original image and the image converted to the current palette on the sidebar
- Independently resize each image using the anchor on the bottom right of each image window (Does not effect output scale)
- Drag and reposition each image window by dragging the top 'bar'
- Change the palette by selecting a preset from the dropdown or manually set any color using the color pickers to the left
- Paste a hex string ("palette key") into the text box below the preset-dropdown and press ENTER to update the palette (for importing custom palettes)
- Palette key is a 96-character string where each 6 digits (0-F) represent a palette color (6x16 colors = 96 characters)
- Invalid palette strings are ignored, keeping the current palette.
- Output image is updated with new palette when any palette color changes
- When output image is re-colored, ORIGINAL image is used for closest color to new palette
- 'Processing...' overlay covers the screen during processing to prevent excessive calculations (mainly when drag-selecting colors within the color-picker widgets)

## Copy Sprite Data
- Splits the image into 8x8 sprites and copies to your clipboard, in TIC-80 sprite format
- Clipboard contains all of the sprites, properly separated with '\n'
- Specify the start/offset tile index with regards to the output data (WIP feature)
- App starts the tile/sprite index at 255 (sprite page) and keeps the tiles in order (viewed from sprite editor) unless > 128x128
- * See example images below

![sprite_data_example_github](https://user-images.githubusercontent.com/25288625/227044658-81c94e91-8593-4e9a-a7a3-2b83bdaaf24f.PNG)

## Output
- Paste the sprite data between the two `<SPRITES> </SPRITES>` tags in your TIC-80 file, and reload your file to see the converted sprites.

![image](https://user-images.githubusercontent.com/25288625/227029707-522adcec-e08e-4416-926e-c6abdc1f8434.png)

## Copy Pixel Data
- Similar to above function, except it outputs a 1-dimensional table of all the pixels (converted to palette indices)
- For drawing arbitrary sized images, 240x136 or smaller. (possibly larger using panning?)
- Accompanied by a drawing function to draw each pixel to the screen using pix() (WIP Feature)


## Side Notes...
- The program is not 100% complete, so expect possible bugs (although I haven't found any major ones testing)
- Note the features (WIP feature) at the end are not finished...
- The copy pixel data button works fine, but for now you will have to write your own function to use pix() to draw each pixel using the output data.
- Please, any feature/s you would like, open a discussion or pull request, or message me in the tic80 discord and I will consider implementing them.
