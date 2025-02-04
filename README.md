# Facer

Face detection, alignment, and averaging using OpenCV and `dlib`.

Facer draws heavily on [this tutorial](https://www.learnopencv.com/average-face-opencv-c-python-tutorial/) from [Satya Mallick](https://github.com/spmallick). I had to update the code pretty heavily to get the project to work, so I thought I'd share my modifications.

# Installation
You have my 100% money-back guarantee that the most difficult part of using this package is installing its requirements. Once you've got OpenCV installed, the rest will be smooth sailing.

## OpenCV
On Mac, use [`homebrew`](https://brew.sh) to install OpenCV. On Windows, I have no clue. Sorry.

```shell
brew install opencv
```

Using `brew` to install OpenCV did actually work for me, but it also broke my previous Python installation and all my virtual environments. So uhh, good luck with that.

## Python packages
After installing OpenCV, use `pip` to install `dlib`, `matplotlib`, and `numpy` from the `requirements.txt` file.

```
pip install -r requirements.txt
```

### Pre-trained detection model
The face landmark detection relies on a pre-trained model that must be downloaded separately from the `dlib` package itself.

```shell
wget http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2
```

Unzip the compressed file after it finishes downloading and move it into the `./Facer/dlib` directory.

# Usage
```python
from facer import facer

# Load face images
path_to_images = "./face_images"
images = facer.load_images(path_to_images)

# Detect landmarks for each face
landmarks, faces = facer.detect_face_landmarks(images)

# Use  the detected landmarks to create an average face
average_face = facer.create_average_face(faces, landmarks, save_image=True)

# View the composite image
plt.imshow(average_face)
plt.show()
```

## Use Vagrant VM
Install (vagrant)[https://www.vagrantup.com/docs/installation/]
```bash
vagrant up
```

Facer also supports creating animated GIFs of the averaging process:

```python
from facer import facer

path_to_images = "./face_images"
gif, average_face = facer.create_animated_gif(path_to_images)
```
