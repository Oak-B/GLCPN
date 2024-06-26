# GLCPN
This is the supplementary file, PyTorch implementation, and prepared datasets for the paper entitled “Graph Linear Convolution Pooling for Learning in Incomplete High-Dimensional Data”. 

## GLCPN-Supplementary File.pdf
The supplementary model discussions including proofs, details of experimental settings, additional experimental results are put into this file and cited.

## GLCPN-Codes.zip
This is the PyTorch implementation for our proposed GLCPN model.

### Code Directory

- GLCPN/
  - model/
    - GLCPN_bi.py # GLCPN implemented for bipartite graphs, such as a QoS network.  
    - GLCPN_ui.py # GLCPN implemented for unipartite graphs, such as a PPI network. 
  - utils/
    - eval.py # Evaluation metrics
    - LoadData_bi.py # Data reading file for bipartite graphs.
    - LoadData_ui.py # Data reading file for unipartite graphs.
  - results/ # Folder for storing experimental results.
- run_bi.py # Executable file for bipartite graphs.
- run_ui.py # Executable file for unipartite graphs.

### Experimental Enviornment
We implement all the experiments in Python 3.7, and deploy them on a server with one 2.4-GHz Intel Xeon 4214R CPU, four NVIDIA RTX 3090 GPUs, and 128-GB RAM. 
We may create an environment using: `conda create --name <env> --file requirements.txt`, or install the required packages using: `conda install --file requirements.txt`.

## GLCPN-Datasets.zip
This file contains all the prepared datasets used in our paper. 
- PPI networks: [T-208964](https://version-12-0.string-db.org/organism/208964), [T-227321](https://version-12-0.string-db.org/organism/227321), [T-9544](https://version-12-0.string-db.org/organism/9544), and [T-9796](https://version-12-0.string-db.org/organism/9796) are undirected PPI networks gathered from the protein interactome database STRING. They respectively record the protein-protein interactions for the species Macaca mulatta, Equus caballus, Pseudomonas aeruginosa, and Aspergillus nidulans. In a PPI network, the nodes represent specific proteins, the edges represent the observed protein-protein interactions, and the weights represent the confidences of interactomes between proteins. All the weight values have been normalized to the range between 0 and 1. T-208964 consists of 5,565 proteins and 1,559,616 interactomes; T-227321 consists of 7,963 proteins and 1,120,030 interactomes; T-9544 consists of 20,462 proteins and 15,597,778 interactomes; and T-9796 consists of 19,664 proteins and 12,149,608 interactomes. Their densities are respectively 5.04%, 1.77%, 3.73%, and 3.14%.
- Scientific collaboration networks: [Astro-Ph](https://sparse.tamu.edu/Newman/astro-ph), [Cond-Mat](https://sparse.tamu.edu/Newman/cond-mat), [Cond-Mat-2003](https://sparse.tamu.edu/Newman/cond-mat-2003), and [Cond-Mat-2005](https://sparse.tamu.edu/Newman/cond-mat-2005) are from the incomplete matrix collection of University of Florida, which describe the co-authorships between scientists posting preprints on the archives of astrophysics (Astro-Ph) and condensed matter (Cond-Mat) at www.arxiv.org in different periods. To be specific, Astro-Ph and Cond-Mat record the co-authorships between Jan. 1, 1995 and Dec. 31, 1999; Cond-Mat-2003 includes all preprints posted between Jan. 1, 1995 and June 30, 2003; and Cond-Mat-2005 includes the co-authorship records between Jan. 1, 1995 and Mar. 31, 2005. The undirected networks are weighted, and the weights are assigned as described in their original papers. Astro-Ph consists of 16,706 nodes (i.e., the involved scientists) and 242,502 edges (i.e., the collaborations); Cond-Mat consists of 16,726 nodes and 95,188 edges; Cond-Mat-2003 consists of 31,163 nodes and 240,058 edges; and Cond-Mat-2005 consists of 40,421 nodes and 351,382 edges. They are all sparse and the densities are only 0.09%, 0.03%, 0.02%, and 0.02%.
- QoS network: [Throughput](https://wsdream.github.io/dataset/wsdream_dataset1.html) is collected by the WS-Dream system, which records the throughputs of cloud services invoked by users. It reflects the fundamental QoS on the user side and is known as one of the most widely-used public QoS datasets in the communication of service computing. This is a bipartite graph including 339 users, 5,825 cloud services, and 1,831,253 invocation records. Its density reaches 92.74%, which is hard to achieve in most of real application scenarios. Hence, we employ random sampling of test cases that include a variety of low-density data split ratios for train-validation-test, i.e., 10%-70%-20%, 20%-60%-20%, 30%-50%-20%, and 40%-40%-20%. This approach enables us to perform an exhaustive evaluation of all models’ representation learning effectiveness in HDI data with a broad range of density conditions.
- DPI network: [Kiba](https://researchportal.helsinki.fi/en/datasets/kiba-a-benchmark-dataset-for-drug-target-prediction) is a benchmark dataset for predicting the binding affinity between drugs and targets, which is created by Jing Tang at the University of Helsinki. It encompasses joint kinase inhibitor bioactivities from various sources including Kd, Ki, and IC50. For training and prediction purposes, the weights are processed into logarithmically normalized KIBA scores. This dataset consists of 118,254 DPI pairs, 2,111 chemical compounds, and 229 kinase targets, resulting a density of 24.46%.

## Others
Please see more information in the manuscript. For further questions not addressed in the manuscript, please feel free to email us at `bifanghui@cigit.ac.cn` for clarification or leave a comment [here](https://github.com/Oak-B/GLCPN/issues).
