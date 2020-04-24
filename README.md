# eo-learn workshop: machine learning in land cover classification with multispectral satellite imagery

This workshop focuses on a particular problem in the field of Earth observation (EO), with the aim of showcasing the [`eo-learn`](https://eo-learn.readthedocs.io/en/latest/) Python library.

It is based on one of the examples from the developer's [public repository](https://github.com/sentinel-hub/eo-learn/tree/master/examples/land-cover-map) and simulates a full processing pipeline.

General instructions before starting the workshop are written below. Once the contents are uploaded in full, you will be able to run through it by yourself by following the notebooks in this repository.



## Minimum requirements

Working with satellite imagery can be inherently challenging due to large amounts of data that needs to be processed. As this is only an example, the data is more manageable, although memory-related issues can still arise. While the contents have been successfully tested on a Linux machine with only 4 GB of RAM, it is recommended that you use a machine with more RAM at your disposal.



## Set-up

`eo-learn` can be installed through [`conda`](https://anaconda.org/conda-forge/eo-learn) or [`pip`](https://pypi.org/project/eo-learn/).

Using [Anaconda](https://www.anaconda.com/distribution/) is recommended, as it is generally convenient for scientific computing and data science. In any case, a 64-bit Python environment of version `>=3.6` is required.

On Linux, it is recommended that you first install the following system packages (per the [build instructions](https://github.com/sentinel-hub/eo-learn/blob/master/.travis.yml#L12)):
```bash
$ sudo apt-get install -y libgdal-dev
$ sudo apt-get install graphviz
$ sudo apt-get install proj-bin
$ sudo apt-get install gcc
$ sudo apt-get install libproj-dev
```


### Installing with `conda`

Install Anaconda by following [the instructions](https://docs.anaconda.com/anaconda/install/) for your operating system. If already installed, you may want to update it with:
```bash
$ conda update
$ conda update conda
$ conda update conda-build
```

Create and activate an isolated environment with:
```bash
$ conda create --name myenv
$ conda activate myenv
```

`eo-learn` can then be installed from `conda-forge` as follows:


```bash
$ conda config --add channels conda-forge
$ conda install -c conda-forge eo-learn
```

**Note:** On Windows, at least, you may experience some issues relating to the `libssl-1_1-x64.dll` and `libcrypto-1_1.dll` files:
- If prevented from updating or downloading new packages, the [solution](https://github.com/conda/conda/issues/9003#issuecomment-516499958) may be to overwrite the instance of `libssl-1_1-x64.dll` in `Anaconda3\Library\bin` with the instance from `Anaconda3\DLLs`.
- If encountering `"ImportError: DLL load failed while importing _ssl: The specified module could not be found."`, for example, when running `$ jupyter notebook` or `$ python -c "import ssl; print('ok')"` from your environment, the [solution](https://bugs.python.org/issue39344#msg360094) may be to copy the `libcrypto-1_1.dll` and `libssl-1_1.dll` files from `Anaconda3\Library\bin` to `Anaconda3\envs\myenv\DLLs`.


### Installing with `pip`

You can install and create an isolated environment by running:
```bash
$ pip install virtualenv
$ python -m venv myenv
```

The environemnt can be activated by running `$ myenv\Scripts\activate.bat` on Windows and `$ source myenv/bin/activate` otherwise.

Once activated, install `eo-learn` with:
```bash
$ pip install eo-learn
```

**Note:** On Windows, if issues are encountered that may be traced to the `gdal`, `rasterio`, `shapely`, `fiona`, or `cartopy` packages, you may need to install them from the [Unofficial Windows wheels repository](https://www.lfd.uci.edu/~gohlke/pythonlibs/), as per the official [installation instructions](https://eo-learn.readthedocs.io/en/latest/install.html).


### Other packages

If Jupyter Notebook was not installed during the process, you can follow the official [installation instructions](https://jupyter.org/install). Once installed, additional [`ipywidgets`](https://ipywidgets.readthedocs.io/en/stable/user_install.html) need to be installed and activated, so that specific elements can be properly displayed.

Using `conda`:
```bash
$ conda install -c conda-forge ipywidgets
```

Using `pip`:
```bash
$ pip install ipywidgets
$ jupyter nbextension enable --py widgetsnbextension --sys-prefix
```

When going through the notebooks, `ipywidgets` may cause some warnings to be raised. These can be ignored:
```
[IPKernelApp] ERROR | No such comm target registered: hv-extension-comm
[IPKernelApp] WARNING | No such comm: hv-extension-comm
```

Finally, `eo-learn` should already include `lightgbm`, an implementation of [Gradient Boosting Decision Trees](https://papers.nips.cc/paper/6907-lightgbm-a-highly-efficient-gradient-boosting-decision-tree), which we will be using for this example. If you are experiencing problems during installation, consult the [LightGBM installation guide](https://lightgbm.readthedocs.io/en/latest/Installation-Guide.html).



## Downloading the materials

Download this repository by clicking the green *Clone or download* button at the top of the page.

To confirm that everything has installed correctly, you can navigate to the directory, where you have extracted the repository to, run `$ jupyter notebook` within your environment, and skim through [notebook 2](https://github.com/JernejPuc/eo-workshop/blob/master/eow-part-2-eo-learn-basics.ipynb). Afterwards, `lightgbm` installation can be verified with `$ python -c "import lightgbm; print('ok')"`.

The data required for the rest of the workshop can be downloaded from eo-learn.sentinel-hub.com.s3.eu-central-1.amazonaws.com/eow_material.zip.



## Contact

For any questions or issues related to the workshop, you can raise an [issue](https://github.com/JernejPuc/eo-workshop/issues) within this repository or send me an [e-mail](mailto:jernej.puc@sinergise.com).

If you have questions regarding `eo-learn` itself or its use cases, you are welcome to send your feedback to its authors, the EO Research team at Sinergise, by:
- raising an [issue](https://github.com/sentinel-hub/eo-learn/issues) on GitHub,
- sending an [e-mail](mailto:eoresearch@sinergise.com),
- opening a topic on the [Sentinel Hub forum](https://forum.sentinel-hub.com/), or
- using any other of the established [Sentinel Hub communication channels](https://sentinel-hub.com/develop/communication-channels).

