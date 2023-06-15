# gnn-x-bench
Benchmarking GNN explainers.

## Requirements

The easiest way to install the dependencies is via [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html). Once you have conda installed, run this command:

```setup
conda env create -f env.yml
```

If you want to install dependencies manually, we tested our code in Python 3.9.7 using the following main dependencies:

- [PyTorch](https://pytorch.org/get-started/locally/) v1.11.0
- [PyTorch Geometric](https://pytorch-geometric.readthedocs.io/en/latest/notes/installation.html) v2.1.0
- [NetworkX](https://networkx.org/documentation/networkx-2.5/install.html) v2.7.1
- [NumPY](https://numpy.org/install/) v1.22.3

Experiments were conducted using the Ubuntu 18.04 operating system on an NVIDIA DGX Station equipped with four V100 GPU cards, each having 128GB of GPU memory. 
The system also included 256GB of RAM and a 20-core Intel Xeon E5-2698 v4 2.2 GHz CPU.

## Usage

### Data installation

Every datasets except for Graph-SST2 is ready to install from PyTorch Geometric libraries. For Graph-SST2, you can download the dataset from 
[here](https://drive.google.com/file/d/1-PiLsjepzT8AboGMYLdVHmmXPpgR8eK1/view?usp=sharing) and put it in `data/` directory.

Then, you can run the following command to preprocess the data. This will preprocess every dataset including generating noisy variants of four datasets.

```setup
python source/data_utils.py
```

### Training Base GNNs

We provide the pretrained models for every dataset and gnn architectures. However, if you want to train the models from scratch, you can run the following command:

```setup
python source/basegnn.py --dataset <dataset_name> --gnn_type <gnn_type> --runs 1
```

We modified GAT, GIN, SAGE implementation of PyTorch Geometric to support our training pipeline. You can find the modified version of the code in `source/wrappers/` directory.


