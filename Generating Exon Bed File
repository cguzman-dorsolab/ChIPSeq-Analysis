*mysql --user=genome --host=genome-mysql.cse.ucsc.edu -A -D hg19 -P 3306 \
    -e "select chrom,txStart,txEnd,K.name,X.geneSymbol,strand,exonStarts,exonEnds \
     from knownGene as K,kgXref as X where  X.kgId=K.name limit 10;" \
| awk 'BEGIN { OFS = "\t"; FS = "\t"}
(NR > 1) {
    delete astarts;
    delete aends;
    split($7, astarts, /,/);
    split($8, aends, /,/);
    sizes=""
    exonCount=0
    for(i=1; i <= length(astarts); i++){
        if (! astarts[i]) continue
        sizes=sizes""(aends[i] - astarts[i])","
    }
    print $1,$2,$3,$5","$4,1,$6,substr(sizes, 1, length(sizes) - 1)
}' > hg19.exon.lengths.bed*

Limits to 10 results for testing purposes, simply remove.
This code can go directly into the command prompt or simply create your own script.
