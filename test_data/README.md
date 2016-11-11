Test files not in repository
============================

Some files are not in the repository as they are publicly available and quite
large. These are the commands to get these files, they must be stored in `test_data` directory
for the tests to find them:

```
cd /path/to/test_data

wget http://hgdownload.cse.ucsc.edu/goldenpath/hg19/chromosomes/chr7.fa.gz 
gunzip chr7.fa.gz
md5sum chr7.fa  ## 30c3693ead968844a769a90a801a900f
samtools faidx chr7.fa
```

**Memo**: If you add more of these files, remember to list them also in `svn_ignore.txt`
and reload the `svn_ignore.txt` files:
 
```
cd /path/to/test_data
svn propset svn:ignore -F svn_ignore.txt .
``` 