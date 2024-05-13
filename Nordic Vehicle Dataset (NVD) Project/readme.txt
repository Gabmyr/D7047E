images/, labels/, test.txt, train.txt, and val.txt belong to the "Labeled Frames" dataset in https://nvd.ltu-ai.dev

yolo9e.pt is obtained via ultralytics library,
see #from ultralytics import YOLO and 
    #model = YOLO("yolov9e.pt")

NVD_Project.ipynb contains
-  Base for YOLO implementation
-  This raw version has rare correct predictions but lots of false negatives and false positives as well
-  Includes object detection with an outer rectangle and a dot in the middle
-  Reads the images from "images" folder ("Labeled Frames" in https://nvd.ltu-ai.dev with size of 24.0 GB) and writes the processed (detected) images to a separate folder called "Processed Images" in the same path
-  Does the process above for every file in the "images" folder 

After this point, I observed the model running (with lots of mistakes) and trying to detect car objects in every image in the images folder, but the accuracy was so poor and needed great tuning. 

NVD_Projectv2 contains a base for the first version and some improvement attempts, which are:
-  Instead of all images, randomly selects 10 images from 8450 images
-  I tried to specify YOLO detection for only cars but not sure if it worked
-  Data augmentation attempt
-  Confidence threshold added
-  Precision and recall calculations added
-  Mean average precision added

After the addition of these functions, I managed to keep the code running and try to detect car edges of 10 images with each run, but the accuracy was no better; it needs better implementation and tuning

