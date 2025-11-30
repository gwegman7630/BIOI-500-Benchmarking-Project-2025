# BIOI-500-Benchmarking-Project-2025
Benchmarking sequence assembly tools Unicycler, SPAdes, and Flye
**Data Generation:**
**SIMULATED DATA:**
Simulated reads were generated using Escherichia coli BL21 reference genome.
Short-read simulation done via ART.
Long-read simulation done via badread.
Each experiment was repeated three times for three replicates.
Short-read mean fragment length always set to 200bp in length.
Long-read mean fragment length always set to 7000bp, 400bp stdev. (See experiment 3).
All assembled at 32 cores.
**EXPERIMENT 1:**
Simulating read quality (accuracy) at varying levels (high, low, and mid). 
Short-reads generated at MSv3 (high quality), HS20 (moderate quality), and GAIIx (poor quality), respectively. 
Long-reads generated at (identity%, stdev) 95,2.5 , 73,10 , and 50,15 respectively.
Short-read coverage always set to 50x.
Long-read coverage always set to 100x.
**HIGH:**
Short-reads: art_illumina -ss MSv3 -i referenceg/BL21.fasta -p -l 200 -f 50 -m 300 -s 3 -o bench_proj/ART/exp1high/rep#_
Long-reads (split into multiple jobs to reduce CPU load and consequently runtime): 
badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > d.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > e.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > f.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > g.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > h.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > i.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > j.fastq & wait & cat a.fastq b.fastq c.fastq d.fastq e.fastq f.fastq g.fastq h.fastq i.fastq j.fastq > bench_proj/badread/exp1high/rep#.fastq
**MID:**
Short-reads: art_illumina -ss HS20 -i referenceg/BL21.fasta -p -l 200 -f 50 -m 300 -s 3 -o bench_proj/ART/exp1mid/rep#_
Long-reads: badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > d.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > e.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > f.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > g.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > h.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > i.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 73,10 --length 7000,400 --error_model nanopore2023 > j.fastq & wait & cat a.fastq b.fastq c.fastq d.fastq e.fastq f.fastq g.fastq h.fastq i.fastq j.fastq > bench_proj/badread/exp1mid/rep1.fastq
**LOW:**
Short-reads: art_illumina -ss GA2 -i referenceg/BL21.fasta -p -l 100 -f 50 -m 300 -s 3 -o bench_proj/ART/exp1low/rep#_
Long-reads: badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > d.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > e.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > f.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > g.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > h.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > i.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --identity 50,15 --length 7000,400 --error_model nanopore2023 > j.fastq & wait & cat a.fastq b.fastq c.fastq d.fastq e.fastq f.fastq g.fastq h.fastq i.fastq j.fastq > bench_proj/badread/exp1low/rep#.fastq
**ASSEMBLY GENERATION:**
Each assembly was generated using each respective quality tier. Ex: Tool assembled using exp2mid short reads replicate 3, and exp2mid long read replicate 3. 
**UNICYCLER:**
/usr/bin/time --verbose unicycler -1 bench_proj/ART/exp2(high mid or low)/rep#_1.fq -2 bench_proj/ART/exp2(high mid or low)/rep#_2.fq -l bench_proj/badread/exp2(high mid or low)/rep#.fastq -t 32 -o bench_proj/unicycler/exp2(high mid or low)/rep#
**FLYE:**
/usr/bin/time --verbose flye --nano-raw bench_proj/badread/exp1(high mid or low)/rep#.fastq --genome-size 4.7m --out-dir bench_proj/flye/exp1(high mid or low)/rep#
**SPADES:**
/usr/bin/time --verbose spades.py -1 bench_proj/ART/exp2(high mid or low)/rep#_1.fq -2 bench_proj/ART/exp2(high mid or low)/rep#_2.fq --nanopore bench_proj/badread/exp2(high mid or low)/rep#.fastq -t 32 -o bench_proj/spades/exp1high/rep#
**Experiment 2**
Simulating read coverage at varying levels (high, mid, low). 
Short-reads generated at 70x, 35x, and 17x, respectively. 
Long-reads generated at 100x, 50x, and 15x, respectively.
Short-reads always set to MSv3.
Long-reads always set to 95, 2.5 (%identity, stdev)
**HIGH:**
Short-reads: art_illumina -ss MSv3 -i referenceg/BL21.fasta -p -l 200 -f 70 -m 300 -s 3 -o bench_proj/ART/exp2high/rep#_
Long-reads: badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > d.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > e.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > f.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > g.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > h.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > i.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > j.fastq & wait & cat a.fastq b.fastq c.fastq d.fastq e.fastq f.fastq g.fastq h.fastq i.fastq j.fastq > bench_proj/badread/exp2high/rep#.fastq
**MID:**
Short-reads: art_illumina -ss MSv3 -i referenceg/BL21.fasta -p -l 200 -f 35 -m 300 -s 3 -o bench_proj/ART/exp2mid/rep#_
Long-reads: badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > d.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > e.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > f.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > g.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > h.fastq badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > i.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > j.fastq & wait & cat a.fastq b.fastq c.fastq d.fastq e.fastq f.fastq g.fastq h.fastq i.fastq j.fastq > bench_proj/badread/exp2mid/rep#.fastq
**LOW:**
Short-reads: art_illumina -ss MSv3 -i referenceg/BL21.fasta -p -l 100 -f 17 -m 300 -s 3 -o bench_proj/ART/exp2low/rep1_
Long-reads: badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > d.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 10x --length 7000,400 --error_model nanopore2023 > e.fastq & wait & cat a.fastq b.fastq c.fastq d.fastq e.fastq > bench_proj/badread/exp2low/rep1.fastq
**ASSEMBLY GENERATION:**
Each assembly was generated using each respective quality tier. Ex: Tool assembled using exp2mid short reads replicate 3, and exp2mid long read replicate 3. 
Experiment 2 low replicate 2 short-reads were used for every experiment 3 assembly.
**UNICYCLER:**
/usr/bin/time --verbose unicycler -1 bench_proj/ART/exp2(high mid or low)/rep#_1.fq -2 bench_proj/ART/exp2(high mid or low)/rep#_2.fq -l bench_proj/badread/exp2(high mid or low)/rep#.fastq -t 32 -o bench_proj/unicycler/exp2(high mid or low)/rep#
**FLYE:**
/usr/bin/time --verbose flye --nano-raw bench_proj/badread/exp2(high mid or low)/rep#.fastq --genome-size 4.7m -t 32 --out-dir bench_proj/flye/exp2(high mid or low)/rep#
**SPADES:**
/usr/bin/time --verbose spades.py -1 bench_proj/ART/exp#(high mid or low)/rep2_1.fq -2 bench_proj/ART/exp#(high mid or low)/rep#_2.fq --nanopore bench_proj/badread/exp2(high mid or low)/rep#.fastq -t 32 -o bench_proj/spades/exp1high/rep#
**EXPERIMENT 3:**
2018: badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 85,5 --length 9600,9600 --error_model nanopore2018 > a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 85,5  --length 9600,9600 --error_model nanopore2018 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 85,5 --length 9600,9600 --error_model nanopore2018 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 85,5 --length 9600,9600 --error_model nanopore2018 > d.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 85,5 --length 9600,9600 --error_model nanopore2018 > e.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 85,5 --length 9600,9600 --error_model nanopore2018 > f.fastq & wait & cat a.fastq b.fastq c.fastq d.fastq e.fastq f.fastq > bench_proj/badread/exp3/2018/rep#.fastq
2024: badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 99,1 --length 6000,1200 --error_model nanopore2023> a.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 99,1  --length 6000,1200 --error_model nanopore2023 > b.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 99,1 --length 6000,1200 --error_model nanopore2023 > c.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 99,1 --length 6000,1200 --error_model nanopore2023 > d.fastq & badread simulate –reference/referenceg/BL21.fasta --quantity 5x --identity 99,1 --length 6000,1200 --error_model nanopore2023 > e.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 99,1 --length 6000,1200 --error_model nanopore2023 > f.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 99,1 --length 6000,1200 --error_model nanopore2023 > g.fastq & badread simulate --reference referenceg/BL21.fasta --quantity 5x --identity 99,1 --length 6000,1200 --error_model nanopore2023 > h.fastq & wait && cat a.fastq b.fastq c.fastq d.fastq e.fastq f.fastq g.fastq h.fastq > bench_proj/badread/exp3/2024/rep1.fastq
**ASSEMBLY GENERATION:**
Each assembly was generated using each respective quality tier. Ex: Tool assembled using exp2mid short reads replicate 3, and exp2mid long read replicate 3. 
Experiment 2 low replicate 2 short-reads were used for every experiment 3 assembly.
**UNICYCLER:**
/usr/bin/time --verbose unicycler -1 bench_proj/ART/exp2(high mid or low)/rep#_1.fq -2 bench_proj/ART/exp3/20(18 or 24)rep#_2.fq -l bench_proj/badread/exp3/20(18 or 24)/rep#.fastq -t 32 -o bench_proj/unicycler/exp3/20(18 or 24)/rep#
**FLYE:**
/usr/bin/time --verbose flye --nano-raw bench_proj/badread/exp3(18 or 24)/rep#.fastq --genome-size 4.7m -t 32 --out-dir bench_proj/flye/exp3/20(18 or 24)/rep#
**SPADES:**
/usr/bin/time --verbose spades.py -1 bench_proj/ART/exp3/20(18 or 24)/rep2_1.fq -2 bench_proj/ART/exp3/20(18 or 24)/rep#_2.fq --nanopore bench_proj/badread/exp3/20(18 or 24)/rep#.fastq -t 32 -o bench_proj/spades/exp3/20(18 or 24)/rep#








