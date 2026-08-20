---
noindex: true
search:
  exclude: true
---

# Python-related

## Setup

- **Install Python on Mac via brew**: <https://docs.python-guide.org/starting/install3/osx/> and set brew python as the default: <https://stackoverflow.com/questions/5157678/how-do-i-use-brew-installed-python-as-the-default-python>
- **Python virtual environment** is detailed here.
- **ML model training tips** are detailed here.

## General

- `super().__init__()` instead of `super(ChildB, self).__init__()`: <https://stackoverflow.com/questions/576169/understanding-python-super-with-init-methods>
- **Issues in loading pickle** related to Python version incompatibility: <https://stackoverflow.com/questions/11305790/pickle-incompatibility-of-numpy-arrays-between-python-2-and-3>
- **Set the spacing between subplots** discussed here. The position of the `*` edge of the subplots is a fraction of the figure width.

```python
plt.subplots_adjust(left=0.1,
                    bottom=0.1,
                    right=0.9,
                    top=0.9,
                    wspace=0.4,
                    hspace=0.4)

plt.tight_layout()  # for automatically maintaining the proper space between subplots
```

## Arrays, strings, images

- **Count nonzero in a numpy array**: <https://stackoverflow.com/questions/18395725/test-if-numpy-array-contains-only-zeros>
- Converting an image from `Image` to (RGB) is equal to converting the image to array. The two images will be the same when we convert them back to `Image` type.
- **Two data structures for storing datasets**: <https://realpython.com/storing-images-in-python/>
- **Convert string to function**: <https://java2blog.com/python-string-to-function/>
- **Regex in Python** is discussed here. A nice, brief tutorial is available here.
- **Sort in Python**: <https://stackoverflow.com/questions/7851077/how-to-return-index-of-a-sorted-list>
- **How to change one char in a string**: <https://stackoverflow.com/questions/1228299/changing-one-character-in-a-string>
- **Histogram for array**: <https://stackoverflow.com/questions/22159160/python-calculate-histogram-of-image>
- **`@` in Python**: <https://stackoverflow.com/questions/6392739/what-does-the-at-symbol-do-in-python>
- **Heatmap on top of image**: <https://stackoverflow.com/questions/42481203/heatmap-on-top-of-image>
- **Colour maps**: <https://matplotlib.org/stable/tutorials/colors/colormaps.html>
- `a[start:end:step]` — Python slicing is explained here: <https://stackoverflow.com/questions/509211/how-slicing-in-python-works>

## OpenCV-related

- **Install**: <https://pypi.org/project/opencv-python/>
- **Contour**: <https://docs.opencv.org/4.x/d4/d73/tutorial_py_contours_begin.html>
- **The image required to `find.contour` method**: <https://stackoverflow.com/questions/63698789/python-opencv-findcontours-error-cpp-197>
- **Convex hull**: <https://docs.opencv.org/4.x/d7/d1d/tutorial_hull.html>
- **Image smoothing**: <https://docs.opencv.org/4.x/d4/d13/tutorial_py_filtering.html>
- **Matplotlib colour**: <https://matplotlib.org/stable/gallery/color/named_colors.html>

## Image, array and array view

- The horizontal and vertical dimensions are the same as what we see in the corresponding images.
- The indices 0-25 are the axis 0 in the array.
- The indices 0-8 are the axis 1 in the array.

## PyTorch

- **Backward hook**: <https://discuss.pytorch.org/t/how-to-modify-conv2d-input-gradients-using-backward-hook/132930/2>
- **Inplace in ReLU**: <https://discuss.pytorch.org/t/whats-the-difference-between-nn-relu-and-nn-relu-inplace-true/948>
- **`to(device)`**: for `nn.Module` or `nn.Parameter`, they will be automatically applied to `to`; for other attributes, they need to be incorporated manually by overriding the `to` function.
- **Make a customised distributed sampler**: <https://discuss.pytorch.org/t/how-to-implement-a-custom-distributed-sampler/151349>

## Install detectron2

```bash
# install python3.10 venv
pip3 install torch torchvision torchaudio
pip3 install 'git+https://github.com/facebookresearch/detectron2.git'

# Install latest LVIS from github
git clone https://github.com/lvis-dataset/lvis-api.git
cd lvis-api
pip install .
```

[Back to Else](index.md)
