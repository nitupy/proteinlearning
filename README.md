<div align="center">
  <a href="https://github.com/">
    <img src="https://user-images.githubusercontent.com/128609917/231207437-1c16b53c-40c1-4d5f-9431-269e2c083816.png" alt="Logo" width="200" height="auto">
  </a>  
  
  <h3 align="center">Protein Function Prediction Using Deep Learning</h3>

  <p align="center">
    Machine Learning 
    <br />
    <a href="https://github.com/"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/">View Demo</a>
    ·
    <a href="https://github.com/othneildrew/">Contact Me</a>
  </p>
</div>


## Project Overiew 👀 
* Protiens are one of the key biochemicals of life and their functions play a crucial role in maintaining the functioning of living organisms. Understanding the function of a protein can allow us to determine how different proteins interact with each other and with other molecules in the human body. This project utilizes deep learning to predict the function of a protein based on its seqeuence of amino acids. 

## Data 📊
* This project utilizes a dataset of protein structures and their corresponding functions from the Protein Data Bank (PDB). The database contains over 170,000 3D structures of proteins and nucelic acids. This data can be used to extract amino acid sequences of proteins and their corresponding functions which can be used to train the deep learning model.

## Applications 🧪
* Protein function prediction is a significant in a wide range of appplications throughout the field of biology. Moreover, by combinging deep learning with biological data, this project can improve the accuracy and speed at which scientists can predict the function of proteins, which is a crucial in the field of bioinformatics. 

## Code 💻 

* Initially, we must extract the amino acid sequences and additional data from the Protein Data Bank

``` python
import urllib.request

# Download the PDB file for a given protein ID
pdb_id = '1AKI'
pdb_url = f'https://files.rcsb.org/download/{pdb_id}.pdb'
urllib.request.urlretrieve(pdb_url, f'{pdb_id}.pdb')

# Extract the amino acid sequence from the PDB file
with open(f'{pdb_id}.pdb', 'r') as f:
    lines = f.readlines()

sequence = ''
for line in lines:
    if line.startswith('SEQRES'):
        sequence += line[19:].strip().replace(' ', '')



```

