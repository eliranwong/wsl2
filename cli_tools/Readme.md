# Common tasks of text processing

To split a single text file into multiple ones, e.g.:<br>
> split -d -l 500 [filename] [optional_prefix_name]

To sort TAB-delimited text file by first 3 columns:<br>
> sort -b -n -t "[TAB HERE]" -k 1,3 test.txt > test2.txt

To add line numbers to text file, starting from number 1:<br>
> nl -nln -v 1 -s "[TAB HERE]" test.txt > test2.txt<br>
[Remarks: -v 1 -s "[TAB HERE]" is implemented by default, could be omitted.]

To change file extensions of multiple files:<br>
> for file in *.html; do mv "$file" "${file%.html}.txt"; done

To add an empty line at the end of a file:<br>
> echo "" >> test.txt

To add an empty line in multiple files:<br>
> for file in *.txt; do echo "" >> $file; done

To combine multiple files in a single file:<br>
> cat *.txt > combined.txt

Tutorial on string manipulation:<br>
https://www.tldp.org/LDP/abs/html/string-manipulation.html

More at: http://www.tldp.org/LDP/abs/html/

# Search & Replace

* Simple:

> sed -E -i.bak 's/[search]/[replace]/g' [file]

e.g. an example of back references:

> echo "test testing" | sed -E 's/(t)(e)s\1/\2/g'

* Dynamic, use the following script:

https://github.com/eliranwong/UniqueBible/blob/master/RegexSearch.py

# sqlite3 Import / Export

Import a TAB-delimited text file into a table:<br>
sqlite3 FILE.sqlite<br>
> .separator "\t"<br>
> .import DATA.csv TABLE<br>
> VACUUM;<br>
> .quit<br>

To export without header:<br>
> sqlite3 -separator "[TAB HERE]" FILE.sqlite "select * from TABLE;" > output_filename.csv

To export with header:<br>
> sqlite3 -header -separator "[TAB HERE]" FILE.sqlite "select * from TABLE;" > output_filename.csv

# Conversion between Traditional and Simplified Chinese

Convert traditional Chinese to simplified Chinese:<br>
> opencc -i [inputFile] -o [outputFile] -c t2s.json

Convert simplified Chinese to traditional Chinese:<br>
> opencc -i [inputFile] -o [outputFile] -c s2t.json

# Download Video / Audio from YouTube

https://github.com/eliranwong/wsl2/blob/master/multimedia/youtube-dl.md
