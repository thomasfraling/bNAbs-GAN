# bnAbs-GAN

Repository for the bachelor thesis entitled *Identification of broadly neutralizing antibodies with a semi-supervised GAN* conducted in the sommer term of 2021 at the ETH Zurich under supervision of Dr. Thomas Lemmin.

In order to run this project the following steps have to be performed:
1. Clone the repository.
2. Run the script `data-preprocessing/data-preprocessing.ipynb` (in the same directory as the repository). This produces several data files, specifically the following python dictionaries:
    - `best_dict`: best neutralizing antibody sequences
    - `best_clusters_dict`: cluster information of the best neutralizing antibody sequences
    - `broad-neutralizing_dict`: broad neutralizing antibody sequences
    - `non-neutralizing_dict`: non-broad neutralizing antibody sequences
    - `UZH_dataset_dict`: antibody sequences from the study conducted by the UZH
    - `simonich_dict`: antibody sequences from the other study
    
    For all dictionaries containing sequences (all the previous ones except `best_clusters_dict`), the dictionary stores a mapping from the assigned sequence key to a dictionary containing the sequence (in amino-acid form), the germline sequence, the CDR3 region and some other sequences specific information (see `relevant_fields` list).
    
    I recommend to use Google Colab, since this allows to store the generated files directly in you own Drive storage (see the variable `source_folder `).
3. Select one experiment and the corresponding notebook. In the variable `datasets_dir` specify the directory in which the previously generated files are stored. Then perform the following steps:
    1. Run the entire script with `use_pretrained = False`. The variable `model_dir` contains the directory where the best model parameters will be saved. Again, for simplicity I recommend to use Google Colab and store the files in your own Drive storage.
    2. The previous step generates a file named e.g. `STATISTICS_trained_on=[baseline]_params=[baseline]` (experiment A). 
    3. Run the code after 'Train and test' setting `use_pretrained = True`. This will generate a file named e.g. `STATISTICS_trained_on=[baseline]_params=[baseline]_using_pretrained` (experiment A). 
    4. These 2 files can be loaded to the directory in which you loaded `visualize-results/visualize_results.ipynb` in order to obatin visualization of the predicitions.
