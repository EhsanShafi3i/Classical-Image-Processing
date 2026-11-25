# Exercise 4 - Background Removal

Run `solution.ipynb` from the project root. It uses OpenCV GrabCut on all five images and saves a binary mask, transparent RGBA PNG, and side-by-side review figure for each image.

For clickable seed selection, run the dependency cell (including ipympl), then use the optional picker cell: set `PICK_IMAGE` to an image filename and run it. Click the image, choose Foreground or Background, undo if needed, and Apply seeds. The new lists are applied in the current kernel and printed for saving in `IMAGE_CONFIGS`.
