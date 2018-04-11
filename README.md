# IMG_psedo_ref_mapping_sorgum_root_meta
# 1. run bbmap
module load bbtools
bbmap.sh nodisk ref=2565956580.fna in=/global/dna/dm_archive/rqc/analyses/AUTO-52257/11408.8.205340.ATCACG.filter-METAGENOME.fastq.gz out=2565956580_Sorghum_microbiome_072115-104_1.sam minid=0.6 cigar=t

# 2. get header from sam files
bash run_get_head.sh

# 3. randomly take 8000 lines from each header
for i in $(ls *_header.txt | cut -d "." -f1) ; do shuf -n 80000 ${i}.txt > ${i}_shuf_rand80000.txt ; done
