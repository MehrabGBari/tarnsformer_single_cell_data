
![image]()
# Project: Geneformer

Geneformer is a foundation transformer model pre-trained on a large-scale corpus of ~30 million single-cell transcriptomes. Please see the details in the [published paper](https://rdcu.be/ddrx0). 

Geneformer was developed on Python and needs to have access to GPUs.  You need to launch an AWS EC2 instance with GPU support.  

## Installation

In the launched container, open a terminal and use the commands listed below to install the Geneformer. 

First, clone the current repo containing the notebooks to run the workflow for fine-tuning Geneformer's pre-trained models.  

```
git clone this repo
cd geneformer_workflow
```

To copy the data used in this workflow into your working directory, run: 

```
mkdir -p input/data
sudo scp -r https://huggingface.co/datasets/ctheodoris/Genecorpus-30M/* input/data/
```

Now install Geneformer from the Hugging Face platform.

```
git clone https://huggingface.co/ctheodoris/Geneformer
cd Geneformer
pip install .

# tdigest is a package used by Geneformer
pip install tdigest 

# PyTorch requires `accelerate>=0.20.1`
pip install accelerate -U
```

Then in the same folder install git-lfs:

```
sudo apt-get install git-lfs
git lfs install
git lfs pull
```

You have now successfully installed the Geneformer, which is ready for use. 

## Run examples

### Fine-tuning toward modelling the perturbation affects

In the `geneformer_workflow/` folder, there are three notebook files; run them by their naming order: 

- Convert single-cell data into loom format for input to geneformer
  - Run `01_preprocess_and_convert_anndata_to_loom.ipynb`
  
- Tokenize inputs using Geneformer's token dictionary file 
  - Run ```02_tokenize.ipynb```
  
- Finetune model
  - Run `03_finetune.ipynb`
  
    
### The tutorial codes
There are some tutorial codes in the `geneformer_workflow/more_examples/` folder. Check if you can run any of them, i.e., `examples/in_silico_perturbation.ipynb`.





