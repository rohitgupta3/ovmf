# Modules

This provides some basic documentation on the modules.

## webcam_input

This module keeps grabbing frames from the webcam and returning them for use further along in the pipeline. It uses the `cv2` package to operate and configure the webcam, setting a number of parameters (fps, frame width and height, exposure, focus, etc). You can optionally have a separate thread taking the image in a loop.

## openface_tracker

This module starts OpenFace using parameters set in contrib.json, and then when it receives the image and data (most importantly the camera's intrinsic parameters) from the webcam_input, it passes these to OpenFace to obtain information on the subject's pose, action units, and facial landmarks.

## image_preview

This module shows a preview of the image grabbed by the webcam_input module and, using the data created by the openface_tracker module, places circles over visible facial landmarks on the image to demonstrate what OpenFace is tracking.

## openface_remapper

This module translates the location captured by OpenFace (by multiplying one of the location coordinates by 2) and scales AU to be within [0, 1]. It also renames the AU names given by OpenFace to avoid zero-padding i.e. it prefers 'AU_1' to 'AU01'.

## smoothing

This module dampens the change over time in action units and pose to avoid unrealistic, overly large movements.

## fexmm_remapper
