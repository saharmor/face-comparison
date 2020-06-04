# face-comparison
AI Face comparison using FaceNet, compare two photos and see if they are the same person.

## Installation
```
pip install face-compare
```

## Usage
Use `compare_faces.py` to compare two images of people to see if they are the same person.
```bash
compare_faces.py --input-one /path/to/image_one.png --input-two /path/to/image_two.png
```

Optionally output the cropped image output to a directory (useful for inspecting input to AI model)
```bash
compare_faces.py --input-one /path/to/image_one.png --input-two /path/to/image_two.png -s /path/to/outputs/
```

## Steps Involved
1. A cascade classifier is used to detect the face within the input images.
2. The bounding box of this segmentation is then used to crop the images, and fed into the AI model.
3. The FaceNet model then calculates the image embeddings for the two cropped images.
4. Finally the second embedding is subtracted from the first, and the Euclidean norm of that vector is calculated.
5. A threshold of 0.7 is used to determine whether they are the same person or not.


## References
This module uses the AI model FaceNet, which can be found [here](https://github.com/davidsandberg/facenet), and the journal article [here](https://arxiv.org/abs/1503.03832).
