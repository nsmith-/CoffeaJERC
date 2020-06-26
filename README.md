# CoffeaJERC
Jet energy resolution and corrections with NANAOD and columnar analysis based on Coffea. 

## Set up a coffea-enabled environment at FNAL

Below, change `<username>` to your user name, `<your_directory>` to your scratch directory. 

Log into `cmslpc`: 

```
ssh -L localhost:8888:localhost:8888  <username>@cmslpc-sl7.fnal.gov
```

Next set cache directory for singularity, go to that directory, and get the docker container for `coffea-dask`: 

```
export SINGULARITY_CACHEDIR=/uscms_data/d2/<your_directory>/singularity/.singularity
cd /uscms_data/d2/<your_directory>/singularity
singularity pull docker://coffeateam/coffea-dask:latest
singularity shell -B ${PWD}:/work docker://coffeateam/coffea-dask:latest
```

From within the container, set the jupyter paths and start a server: 

```
export JUPYTER_PATH=/work/.jupyter
export JUPYTER_RUNTIME_DIR=/work/.local/share/jupyter/runtime
export JUPYTER_DATA_DIR=/work/.local/share/jupyter
export IPYTHONDIR=/work/.ipython
jupyter notebook --ip 0.0.0.0 --no-browser --notebook-dir /work
```


## Execute notebook

Go to [localhost](localhost:8888) to open the jupyter interface. The example notebook is [here](https://github.com/cms-jet/CoffeaJERC/blob/master/genL2L3.ipynb). 

