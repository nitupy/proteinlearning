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

<br></br>

### Prerequisites 🚩

* Understanding of deep learning frameworks such as PyTorch and TensorFlow which are commonly used in projects similar to this 🤖
* Installation of data processing libraries such as NumPy, Pandas, and Scikit-learn that are utilized to analyze and process data 💾
* Strong knowledge in Python, a popular programming language that is used for deep learning and machine learning 🐍
* Strong foundation in biology and basic knowledge of biochemistry to understand the relavence of biology and the application of deep learning in resolving a problem in bioinformatics 🔬

### Links 🔗 
<p align = "center">

<a href="https://www.python.org/doc/">Python Documentation</a>
·
 <a href="https://numpy.org/doc/">NumPy Documentation</a>
·
<a href="https://pandas.pydata.org/docs/Pandas">Pandas Documentation</a>
·
<a href="https://pytorch.org/docs/stable/index.html">PyTorch Documentation</a>
·
<a href="https://scikit-learn.org/stable/">Scikit Documentation</a>
·
<a href="https://www.tensorflow.org/api_docs">TensorFlow Documentation</a>
·
<a href="https://paperswithcode.com/datasets?mod=biology">Biology Datasets</a>


## Methodology ⚙️

### **Extraction**
* Initially, we must extract the amino acid sequences and additional data from the Protein Data Bank. We must then utilize deep learning techniques to extract features from the amino acid sequences to determine the structure of the protein.

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
<br></br>

``` python
import tensorflow as tf
from tensorflow.keras.layers import Conv1D, MaxPooling1D, LSTM, Dense

# Define a CNN to extract features from the amino acid sequence
model = tf.keras.Sequential([
    Conv1D(filters=32, kernel_size=3, activation='relu', input_shape=(len(sequence), 1)),
    MaxPooling1D(pool_size=2),
    Conv1D(filters=64, kernel_size=3, activation='relu'),
    MaxPooling1D(pool_size=2),
    Conv1D(filters=128, kernel_size=3, activation='relu'),
    MaxPooling1D(pool_size=2),
])

# Define an RNN to capture the temporal dependencies in the sequence
model.add(LSTM(units=64))

# Add a fully connected layer to predict the function of the protein
model.add(Dense(units=num_functions, activation='softmax'))


```

