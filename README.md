# formatin.pl
#A simple script to format a genomes database from blastp 
#Making a blast database of all .faa files, change .faa to whatever you use if needed

@fastas=qx/ls|grep .faa/;
foreach (@fastas){
    chomp $_;
    system "makeblastdb -in $_ -dbtype prot -parse_seqids -logfile makeblastdb.log";
    $cont++;
    print "$cont $_ has been added to the blast database\n";

}
