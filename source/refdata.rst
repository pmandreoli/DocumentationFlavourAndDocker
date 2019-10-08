Reference data documentation
============================

CVMFS:

.. csv-table::
   :header: "CVMFS", "Flavours supported", "folder tree" 
   :widths: auto
   :file: _static/table_cvmfs.csv

Common folders between the two CVMFS 
--------------------------------------

the repository first layer of directory are referred to model organism genome different assemblies:

.. hlist::
   :columns: 2
   
   - at10
   - at9
   - dm2
   - dm3
   - dm6
   - hg18
   - hg19
   - hg38
   - mm10
   - mm8
   - mm9
   - sacCer1
   - sacCer2
   - sacCer3

inside every assembly directory there is the genome.fa and the refseq gtf and gff downloaded from ucsc and the indices for the tools:

- bwa: created using the default command 

  .. code:: bash

          ~$ bwa index -a bwtsw genome.fa

- bowtie2: created using the default command 
  

  .. code:: bash

          ~$ bowtie2-build

- bowtie: created using the default command
 
  .. code:: bash

          ~$bowtie-build

- rsem: created using the default command
 
 
  .. code:: bash

          ~$rsem-prepare-reference --gtf (.gtf) --transcript-to-gene-map (table.txt) --bowtie (.fa) <assembly-name> 


additional folders
------------------

elixir-italy.galaxy.refdata
***************************

- rRNAdatabase : location of ribosomial RNA for sortmeRNA tool in galaxyRNAworkbench
- index_GATK_bundle: location of genome indices for GATK toools for hg38 and hg19 assembly downloaded from GATK ftp bundle (https://software.broadinstitute.org/gatk/download/bundle)
- location: contains the .loc file and the tool_data_table.xml file that will be used by galaxyRNAworkbench galaxyEPIGEN and galaxy-GDC

elixir-italy.covacs.refdata
***************************

- annovar_db: contains the databases needed to perform CoVaCS pipeline downloaded from annovar repository using the annotate_variation.pl perl script
- bed_file_covacs: contain the bed files needed to perform CoVacs pipeline, the same bed files were present in the CINECA implementation of the CoVaCS pipeline
- location: contains the .loc file and the tool_data_table.xml file that will be used by galaxy CoVaCS



more information at https://docs.google.com/spreadsheets/d/1l0dbaVuT4qiXMGevrYtkRDvsNa052WT8WbBg_dFpqFM/edit?usp=sharing 

