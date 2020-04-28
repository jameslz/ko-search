## ko-search introduction

Reimplement kofamscan using **hmm-utils** for KEGG Knumber annotation

#### about KofamScan

KofamScan is a gene function annotation tool based on KEGG Orthology and hidden Markov model.

KOfam database: [https://www.genome.jp/tools/kofamkoala/][1]
KofamScan: [https://github.com/takaram/kofam_scan][2]

#### about hmm-utils

    Usage:   hmm-utils <command> <arguments>
    Version: 0.0.1-r1-dirty
    
    Command:
             hmmscan    tabulate hmmscan domtblout.
             hmmsearch  tabulate hmmsearch domtblout.
             domains    domains above score and coverage threshold.
             resolve    resolve overlaped domains.
             best       best HMMER domain.
             title      add tabulate title.
    
          -- kegg utils
             kotab      kofam annotation format.
             kofam      KEGG ortholog annotation.
             metafam    KEGG ortholog annotation for metagenome.
    
          -- hmm files utils
             partition  partition HMM files.
             split      split each HMM profile to individual file.
             fetch      get HMM profile by NAME.
    
    
    Licenced:
    (c) 2020-2020 - LEI ZHANG
    Logic Informatics Co.,Ltd.
    zhanglei@logicinformatics.com

hmm-utils uses kotab as  intermediate file format. kotab includes query coverage and HMM coverage value which can be used to normalize the Kofam threshold value. It's usefull for fragmented sequence. ie. metagenome protein sequence.


#### ko-search interface


    Program: kofam-search: HMM based KEGG KO annotation.
    Version: 0.0.1 r1
    Contact: ZHANG LEI <zhanglei@logicinformatics.com>
    
    Usage:   kofam-search [options] <sequence> <project>
    
    Options: -c int    CPU number, default: [64]
             -p double coverage of domain, default: [0.9]
             -q double coverage of query,  default: [0.9]
             -e double set evalue cutoff,  default: [10.0]
             -t double ko threshold scale, default: [1.0]
             -m        ko assignment for metagenome proteins, default: []
             -s double min score requirement for threshold scale. default: [0.0]
             -k str    kofam database location, default: [/biostack/database/kegg]
                       include profiles and ko_list
             -d str    prokaryote|eukaryote|kofams, default: [kofams]


the default parameters of  kofam-search is the same way with kofanscan. (evalue 10, threshold scale 1.0).

### download db
   
    wget ftp://ftp.genome.jp/pub/db/kofam/profiles.tar.gz
    wget ftp://ftp.genome.jp/pub/db/kofam/ko_list.gz
    tar xzvf profiles.tar.gz
    gunzip ko_list.gz


  [1]: https://www.genome.jp/tools/kofamkoala/
  [2]: https://github.com/takaram/kofam_scan
