# Stereoscopic

Assuming stereoscopic .gifs are composed of a sequence of simultaneous images taken at a slight angle offset, then played back at a short duration per frame < 0.5s, it could reproduce the bullet-time effect. Using a Python backend, images can be stitched together into .gifs using the **imageio** package, used as such (for example):

```python
with imageio.get_writer("file.gif", mode='I', duration=0.1) as writer:
	for filename in filenames:
		image = imageio.imread(filename)
		image = imutils.resize(image, width=600)
		writer.append_data(image)
```
It may be possible to interpolate between two photos (known as *tweening*), using the **OpenCV** library. I've experimented with feature detection using FREAK and ORB algorithms (I've avoided SIFT since it seems to be proprietary). This makes it possible to find common points between two photos. Another way to do this is the Lucas Kanade or dense optical flow algorithms, which detect moving objects between frames. Although this finds more points of interest, it also appears more unstable. Interpolation works with some visible glitches in the image. This is obviously undesirable and needs to be perfected.

## Dependencies ##

**imutils** - for scaling images
**imageio** - for gif creation
**opencv** - for image processing

## Authors

**Jonathan Chang** - [jachang820](https://github.com/jachang820)