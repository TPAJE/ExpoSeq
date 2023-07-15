# Welcome to ExpoSeq

ExpoSeq is a powerful pipeline for processing and analyzing FASTQ files from sequencing phage Display panning samples.It utilizes [MiXCR](https://docs.milaboratories.com/mixcr/getting-started/installation/) to align and assemble the data which you can subsequently analyze in multiple plots. The pipeline focuses on analysing the identity between samples but also applies various clustering techniques to analyse the relation between the sequences. Besides, you can add binding data to relate the clusters to affinity.  ![overview](pictures_gen/expoSeq_overview.png)

## Installation

Open a virtual environment and type ```pip install ExpoSeq```. Ensure that you have python > 3.11 installed.

To get started, please download and follow the instructions for MiXCR under the following link: https://docs.milaboratories.com/mixcr/getting-started/installation/ 
You can also only use the test version without installing it.

## Importing the Plotting Tool

To access the plotting tool, you will need to import it into your console by running the following command:
```from ExpoSeq.pipeline import PlotManager```

If you want to use the fast and easy version you can ignore the rest of the instructions and just import in your Console:
```import ExpoSeq.run```
## Using the PlotManager

The PlotManager is the main interface for creating various plots using your FASTQ data. You can create an instance of the PlotManager by running the following command:
```plot = PlotManager()```
To use the PlotManager to create plots, you will need to upload your FASTQ data to the pipeline. This will automatically happen as soon as you have called the PlotManager. In the following you can obtain an insight in the worklow of the pipeline after the initial call. There, the blue boxes indicate your input, gray are optional inputs while black and red are processing steps and output, respectively.
![relative_path_to_image](pictures_gen/workflow_ExpoSeq.png)
If you just want to test the pipeline and see its functions you can call: ```plot = PlotManager(test_version = True)```

Once you have called the test version or have finished the data processing, you can use the PlotManager to create a variety of plots, such as an identity plot based on the jaccard similarity. Here is an example of how to create this type of plot:
```plot.jaccard()```
If you want to change the style of the plot you can use the PlotManager. If you called it ```plot``` you can do for instance the following: ```plot.style.title_xaxis("your_title")``` 
If you want to implement further plot change you can also refer to the matplotlib.pyplot library and change it in the same way as following:
```import matplotlib.pyplot as plt```
```plt.xlabel("your_title")```
If you would like to have details about the inputs and functions of the PlotManager call: ```help(plot)``` . You can also call ```help(plot.jaccard)```


## Process fastq files with mixcr on a server
If you would like to process your data on a server to make use of multithreading or process on a screen in a background you can use the scripts in the folder bash_processing. Copy the folder and the folder with the mixcr.jar file to the corresponding directory. You can use the script: run_mixcr.sh to generate a sequencing report which is the input of the pipeline. The script needs to inputs and you can give optional inputs such as the number of threads you want to use. The inputs are listed in the following:
--fastq_directory: directory to your fastq files
--path_to_mixcr: filepath with .jar ending to mixcr 
--save_dir: directory where you would like to store the sequencing report (optional: default is the working directory)
--paired_end_sequencing: Boolean whether you have paired end sequencing data or not (optional: default is False)
--threads: number of threads you would like to utilize (optional: default is 1)
--method: mixcr method to assemble and align your sequences (optional: default is milab-human-tcr-dna-multiplex-cdr3)
--trim_div_by: all sequences are trimmed which are divisble by the integer you input (optional: default is 3)
--trim_min_count: all sequences are trimmed which are shorter than the given integer (optional: default is 3)


## References
[1] Dmitriy A. Bolotin, Stanislav Poslavsky, Igor Mitrophanov, Mikhail Shugay, Ilgar Z. Mamedov, Ekaterina V. Putintseva, and Dmitriy M. Chudakov. "MiXCR: software for comprehensive adaptive immunity profiling." Nature methods 12, no. 5 (2015): 380-381.


[2] Dmitriy A. Bolotin, Stanislav Poslavsky, Alexey N. Davydov, Felix E. Frenkel, Lorenzo Fanchi, Olga I. Zolotareva, Saskia Hemmers, Ekaterina V. Putintseva, Anna S. Obraztsova, Mikhail Shugay, Ravshan I. Ataullakhanov, Alexander Y. Rudensky, Ton N. Schumacher & Dmitriy M. Chudakov. "Antigen receptor repertoire profiling from RNA-seq data." Nature Biotechnology 35, 908–911 (2017)

[3] (1, 2) Tareen A, Kinney JB (2019) Logomaker: beautiful sequence logos in Python. Bioinformatics btz921. bioRxiv doi:10.1101/635029.




