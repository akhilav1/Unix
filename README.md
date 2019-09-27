# UNIX Assignment

# Data Inspection

# Attributes of fang_et_al_genotypes

here is my snippet of code used for data inspection

$ du -h fang_et_al_genotypes.txt for file size

$ awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt for number of columns

$ wc -l fang_et_al_genotypes.txt for number of lines

By inspecting this file I learned that:

 1. 6.1M size
 2. 2783 lines
 3. 984 columns


# Attributes of snp_position.txt

here is my snippet of code used for data inspection

du -h snp_position.txt for file size

awk -F "\t" '{print NF; exit}' snp_position.txt for columns

wc -l snp_position.txt for number of lines


By inspecting this file I learned that:

1. 38K size
2. 15  columns
3. 984 lines


# Data Processing

# Maize Data
For extracting data

code to examine column 3 of fang_et al

sort -k3 fang_ et_ genotypes.ext | cut -f -3| uniq -c |
column -t | wc -l

awk -F "\t" '$3 ~ /Group|ZMMIL|ZMMLR|ZMMMR/' fang _et _al _genotypes.txt | cut -f 1,4-986 > maizegen.txt

#for sorting after transposition 

(head -n 1 transposed _maizegen.txt && tail -n +2 transposed _maizegen.txt |sort -k1,1) > sort _transposed _maizegen.txt


# Teosinte Data
for extracting data

awk -F "\t" '$3 ~ /Group|ZMPBA|ZMPIL|ZMMPJA/' snp _position.txt | cut -f 1,4-986 > teosintegen.txt


# for sorting after transposition 

(head -n 1 transposed _teosintegen.txt && tail -n +2 transposed _teosintegen.txt |sort -k1,1) > sort _transposed _teosintegen.txt

 To get column 1,3,4 in snp_position  
cut -f 1,3,4 snp _position.txt > cut _snp _position.txt

# Sort without header
(head -n 1 cut _snp _position.txt && tail -n +2 cut _snp _ posiion.txt |sort -k1,1) > sort _cut _snp _position.txt

# To Join files
join -1 1 -2 1 --header sort _cut _snp _position.txt -t $'\t' sort _transposed _teosintegen.txt >joined _teosintegen.txt

join -1 1 -2 1 --header sort _cut _snp _position.txt -t $'\t' sort _transposed _maizegen.txt >joined _maizegen.txt




