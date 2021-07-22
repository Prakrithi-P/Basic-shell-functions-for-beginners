AWK , grep, sed, cat basics

To remove a col and print op as tab delimited
>awk ‘BEGIN{OFS= “\t”}!($1=” ”)’ ip.txt > op.txt   ======= ($1 is the col to be removed)

To split a col into sub cols : 
>cat ip.txt | awk ‘{split($1,a,”_”); printf(“%s\t%s\t%s\t%s\t%s\t%s\n”, a[1],a[2],a[3],a[4],a[5], $2);}’ > op.txt

( before: 1_1234_C_T_ENS4000_4
After: 1	1234	C	T	ENS4000	4	)

To convert row to col (transpose)
> awk ‘{for (i=1;i<=NF;i++) print $i}’ ip > op

Or 
> awk ‘BEGIN{OFS= “\n”}{for (i=1;i<=NR;i++) print $i}’ ip > op

To paste 1,2column of a file to 3rdcol of same file
awk 'BEGIN{FS="\t"; OFS="\t"} {$3=$1"\:"$2; print}' ip  | awk '!/#/ {print }' > op

To replace new line with space or tab:
tr ‘\n’ ‘\t’ <ip > op  === (‘ ‘ for space)

To count lines in a file
> wc -l filename

To sort a file based on col1
> sort -u -k 1 ip > op

Sort decending order on col 3 (g considers exponential values while using n does not)
> sort -rg -t $'\t' -k3,3 ip > op

To insert line in 1st line of file
> sed -i '1i\first_line_text’ ip

To delete 2nd and 3rd row in a file
> sed '2,3d' ip > op

To remove excess space bw cols
> sed -E ‘s /[ ][ ]+/\\t /g’ ip > op

To match words from f1 in f2
>grep -wFf f1 f2 > op

To print only SNPs from SV file
>awk ‘length($4)==1 && /rs/ {print } ip > op

(/**/ - To print all lines having the specifies text , Since indels are also named as rs###, column four (length of allele) is 1 for SNPs and can be filtered)

To add ‘chr’ to col1 of a file
> sed ‘s/^/chr/’ ip > op

To replace rsID column with dot
>sed -i "/^[^#]/s/rs[0-9]\+/./g" ip > op

To add a column with the same value in all rows
>nawk '$1=(FNR FS $1)'  ip > op       ======== FNR=22 to add 22 in all rows


To print col1 if col 2 satisfies a criterion
>awk ‘$2 < 0.5 {print $1}’ ip > op

To print variants within a specified coordinate
>awk ‘$2>1000 && $2<2000 {print $3 }’ ip.vcf > SNP.txt

To replace a word in a file with another
> sed -i ‘s/originalword/newword/g’ ip> op

To replace 3rd col in a file with file2-col1
awk 'NR==FNR{a[NR]=$1;next} {$3=a[FNR]}1' OFS="\t" test2.txt test1.txt

To count no. of columns in a tab separated file
>awk -F'\t' '{print NF; exit}' ip

To add “ ” for every field separated by space
>awk '{for (i=1;i<=NF;i++) $i="\""$i"\""}1' FS=" " OFS=" " input > op

To add comma after each field
>awk '{for(i=1;i<NF;i++)if(i!=NF){$i=$i","}  }1' ip > op

To convert csv to tab delimited
> sed 's/\,/\t/g' ip > op

Print lines If entry in a column is not equal to a non-numeric char
> awk '{if ($5!="\-") print }' ip> op

(if col 5 is  not eql to -)

To download all files in a link
> wget -A gz -m -p -E -k -K -np link (-A accept file type of gz or jpg or pdf)

Awk with compressed files
> awk '{ ... }' <(gzip -dc ip.file.gz) | gzip > op.file.gz

To print ranges of consequitive positions in a list
awk '   function output() { print start (prev == start ? "" : ","prev) }
	NR == 2 {start = prev = $2; next}
	$2 > prev+1 {output(); start = $2}
	{prev = $2}
	END {output()} ' tastemultiannochrpos.txt | awk '/,/ {print }' > consequitivepos.txt

To swap 1st 2 cols
>awk '{ t = $1; $1 = $2; $2 = t; print; }' ip > op

To remove first two columns in a file:
>cut -d " " -f 3- input_filename > output_filename

Extract .bz2 files
bunzip2 ip 

Extract tar.bz2
Tar -xf ip

To delete 0bytes files
Find -size 0 -type f -delete
