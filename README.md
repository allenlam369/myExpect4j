myExpect4j
================================================================================== 
for creating a review file of any datatype in Millennium ILS from a text file of data, without relying on the UI of Mil


## A. INTRODUCTION

1. This program reads an input file of ISBN/ISSN list (one number each line)
2. It tries to find a matching bib record from Innopac
3. It reports the bib record number and bib mat-format (book or ebook)
4. If you define operation mode=e, it also captures the first MARC TAG 092


## B. INSTALL
1. copy the folder "isn2bib" to your local hard disk, under any directory you like
2. make sure you have java 1.6 or above installed
3. to check your java version, open a command prompt, type in "java -version"


## C. DEFINE INPUT/OUTPUT
1. use any text editor to edit genList.ini
2. define 
- mode [e|p|all]
- infilename
- outfilename
3. Put your input file under isn2bib/data
4. The ouput file will be written under isn2bib/data


## D. MEANING OF MODES
p: printed books (Speed: medium)
When there are multiple matching of the ISN, it tries to limit the search by "book" and reports the first finding.
If only ebooks are available it reports the first ebook.

e: ebooks (Speed: slow)
When there are multiple matching of the ISN, it tries to limit the search by "ebook" and reports the first finding.
If only printed books are available it reports the first printed book.
It will further detect the first Marc092 (call number or ebook vendor) and report.

all: both p and e (Speed: fast)
All matching results are listed, delimited by ';'
Each result is marked with (book) or (ebook)


## E. RUN PROGRAM
1. define input/output in genList.ini file
2. open a command prompt, cd to isn2bib
3. java -jar Isn2Bib.jar
4. go to data directory to find your output file
5. the fields in the output file are delimited by TAB


## F. RUNTIME ERROR
In case of runtime error (e.g. caused by network delay, server response delay, unexpected record sturctures, etc),
it reports "Error getting search result" in its finding and continues the next search.
You can pick out those failed lines into a separate input file and try again, or process them manually.

