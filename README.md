# LIBD75

Base-calling


Assembly
Flye:
flye --nano-raw path-of-lr-fastq -g 3g -o flye -t 30

Hapdup:
HD_DIR=/nfs/turbo/umms-smaht/working/202402_assembly/wholerun/
minimap2 -ax map-ont -t 30 $HD_DIR/flye/assembly.fasta path-of-lr-fastq | samtools sort -@ 4 -m 4G > $HD_DIR/hapdup/lr_mapping.bam
samtools index -@ 4 $HD_DIR/hapdup/lr_mapping.bam

singularity exec --bind $HD_DIR hapdup_0.12.sif hapdup --assembly $HD_DIR/flye/assembly.fasta --bam $HD_DIR/hapdup/lr_mapping.bam --out-dir hapdup -t 24 --rtype ont
![image](https://github.com/WeichenZhou/LIBD75/assets/56660809/6523c71d-668f-476c-b704-3a809b4ea73d)



Alignment


Genetic Variant calling


Data analysis


