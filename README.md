# Machine Learning Courses

A repository containing Introduction to Machine Learning Course, Advanced Machine Learning Course, and Deep Learning Notes and Projects.

## Setup

We use Python, Conda, and the usual machine learning packages for this class.

You can also use Anaconda for Windows + VSCode, Collabera, etc.

```
  sudo pacman -S python3 python-pip pythonA
  yay -S python-conda jupyterlab jupyter-notebook
  # Create a conda environment named ml for machine learning
  conda create -n "ml"
  sudo conda init bash
  # Re-exec bash, enter the venv
  bash
  conda activate ml
  # Get all the ml packages
  conda install --yes numpy scipy pandas scikit-learn matplotlib seaborn
  # Update conda
  conda update -n base conda
  # To use the system env versus the conda 'base' env on startup
  conda config --set auto_activate_base false
```

See: github.com/bbullman/dotfiles for more installation instructions on various OS and environments.

## Directories

* The Class Notes directory is a structured markdown wiki using Obsidian.
* Books contains free resources including the ISLP
* Machine Learning contains labs, exercises, case studies, and datasets for the base class
* Machine Learning (Advanced) contains labs, exercises, case studies, for the advanced class
* Deep Learning contains labs, exercises, case studies, for the deep learning class
