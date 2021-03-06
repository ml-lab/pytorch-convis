# convis
A tool to visualize convolutional layer activations on an input image. This is a PyTorch implementation of [convis](https://github.com/htoyryla/convis).


An output image from a single channel (left), and a layer heatmap (right): 
<div align="center">
<img src="https://raw.githubusercontent.com/ProGamerGov/pytorch-convis/master/examples/output/tubingen-conv3_2-16.jpg" height="250px">
<img src="https://raw.githubusercontent.com/ProGamerGov/pytorch-convis/master/examples/output/tubingen_vgg19_relu4_2_heatmap.jpg" height="250px">
</div>

### Dependencies:

PyTorch 

### Setup: 

After installing the dependencies, you'll need to run the following script to download the default VGG and NIN models:

```
python models/download_models.py
```

You can also place `convis.py` or `convis_heatmap.py` in your neural-style-pt directory, in order to to more easily work with models and input images. 

### Usage:

`convis.py` will create an output image for every channel in the specified layer:

```
python convis.py -image examples/inputs/tubingen.jpg -model models/vgg19-d01eb7cb.pth -layer conv2_2 -output_dir output -seed 876
```

`convis_heatmap.py` will create a single output image composed of every channel in the specified layer:

```
python convis_heatmap.py -image examples/inputs/tubingen.jpg -model models/vgg19-d01eb7cb.pth -layer relu4_2 -seed 876
```
 
### Parameters:

* `-input_image`: Path to the input image.
* `-image_size`: Maximum side length (in pixels) of of the generated image. Default is 512.
* `-layer`: The target layer. Default is `relu4_2`
* `-seed`: An optional value which makes all random values deterministic. 
* `-pooling`: The type of pooling layers to use; one of `max` or `avg`. Default is `max`.
* `-model_file`: Path to the `.pth` file for the VGG or NIN model.
* `-output_image`: Name of the output image. Default is `out.png`.
* `-output_dir`: Name of the output image directory. Default is `output`.

The output files will be named like `output/tubingen-conv3_2-69.png`
