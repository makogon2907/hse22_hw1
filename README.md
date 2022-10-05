### Создаю подпапку в домашней папке для работы
```bash
mkdir hw1
cd hw1
```

### Создаем символические ссылки на общие файлы

```bash
ln -s /usr/share/data-minor-bioinf/assembly/oil_R1.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oil_R2.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R1_001.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R2_001.fastq
```


### Случайно выбираем 5 миллионов paired-end чтений и 1.5 миллиона mate-pairs чтений:

```bash
seqtk sample -s729 oil_R1.fastq 5000000 > Paired1.fastq
seqtk sample -s729 oil_R2.fastq 5000000 > Paired2.fastq
seqtk sample -s729 oilMP_S4_L001_R1_001.fastq 1500000 > Mate1.fastq
seqtk sample -s729 oilMP_S4_L001_R2_001.fastq 1500000 > Mate2.fastq
```

### Оцениваем качество исходных чтений с помощью fastqc и получаем статистику с помощью multiqc 

```
mkdir fastqc
fastqc Paired1.fastq Paired2.fastq Mate1.fastq Mate2.fastq -o fastqc
multiqc fastqc -o multiqc_stat
```

### Скриншоты из статистики 