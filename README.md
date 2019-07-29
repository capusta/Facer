# Facer

Python package for simple face detection, alignment, and averaging using `OpenCV` and `dlib`.

# Installation
You have my 100%, money-back guarantee, that the most difficult part of using this package is installing the requirements. Once you've got `OpenCV` and `dlib` installed, the rest will be smooth sailing.

## `OpenCV`
On Mac, use [`homebrew`]() to install `OpenCV`. On Windows, I have no clue. Sorry.

```shell
brew install opencv
```

Installing `OpenCV` with `brew` did actually work for me, but it also broke my previous Python installation and all my virtual environments. So uh, good luck with that.

## `dlib`
Installing `dlib` is hopefully straightforward. You can use `pip`:

```shell
pip install dlib
```

### Pre-trained detection models
The face landmark detection relies on a pre-trained model that must be downloaded separately from the `dlib` package itself.

```shell
wget http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2
```

Unzip the compressed file after it finishes downloading.

## Python requirements
After installing `OpenCV` and `dlib`, we just need to add a few more helper libraries.

```
pip install -r requirements.txt
```

# Usage
```python
import facer

# Detect landmarks for each face
path_to_images = "./face_images"
landmarks = facer.detect_face_landmarks(path_to_images)

# Use  the detected landmarks to create an average face
average_face = facer.create_average_face(faces, landmarks, save_image=True)

# View the composite image
plt.imshow(average_face)
plt.show()
```
