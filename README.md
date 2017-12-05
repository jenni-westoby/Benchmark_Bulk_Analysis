# Benchmark_Bulk_Analysis

Prerequisites:

-virtualenv

-github account

-reference genome gtf and fasta files. Note that if your data contains ERRCC spike-ins, you should concatenate the reference genome gtf file with the ERRCC gtf file, and concatenate the reference and ERRCC fastq files (see https://tools.thermofisher.com/content/sfs/manuals/cms_095048.txt)

To run the pipeline:

1. Execute ./setup.sh setup. This will create a new directory called Simulation into which all the software required for this pipeline will be locally installed. In addition, empty directories are created within the Simulation directory which will eventually contain the RSEM references, various indices, the raw and simulated data, results matrices and graphs. This step will take ~30 minutes - 1 hour depending on your network speed.

2. Execute ./RSEM_ref.sh make_ref /path/to/gtf path/to/fasta, where the gtf and fasta files are the reference genome. This builds the RSEM reference.

3. Execute ./simulate.sh run_simulations path/to/raw/data. The simulated bulk RNA-seq data and their ground truth expression values are saved in Simulation/data/simulated.

4. Execute ./benchmark.sh benchmark name_of_program_you_want_to_test. This will generate results matrices of expression values for the method you are interested in. Repeat for each method you want to test.

5. Execute ./make_matrix.sh make_matrix name_of_program_you_want_to_test. This generates a compact results matrix for each method in results_matrices.

6. Execute ./clean_data.sh to trim filename paths from results matrix column names.

