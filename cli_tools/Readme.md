# Common tasks of text processing

To split a single text file into multiple ones, with maximum of 500 lines each, e.g.:<br>
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

* Simple tasks with sed:

> sed -E -i.bak 's/[search]/[replace]/g' [file]

e.g. an example of back references:

> echo "test testing" | sed -E 's/(t)(e)s\1/\2/g'

e.g. executing multiple commands

> echo "test testing" | sed -E -e 's/(t)(e)s\1/\2/g;s/i/I/g'

> sed -E -i.bak -f myScript.sed inputFile.txt

* Simple tasks with awk / gawk:

> echo "My_name_is_Wong" | awk -F '_' '{surname=$4; $4="Eliran"; print $4 " " surname; print $0 " " surname}'

> echo "My_name_is_Wong" | awk -F '_' '{gsub($4,"Eliran_Wong",$0); print$0}'

* A dynamic script written with python:

https://github.com/eliranwong/bible-verse-parser/blob/master/RegexSearch.py

To use the script on its own, edit the content under function 'def processInputText(self, text):' and run:

> python3 RegexSearch.py

or

> python3 RegexSearch.py [a_file_name]

or

> python3 RegexSearch.py [a_folder_name]

To use the script to build other script, for example:

https://github.com/eliranwong/bible-verse-parser/blob/master/BibleVerseParser.py

# rar & unrar

To list files in a rar file, e.g. file.rar:

> unrar l file.rar

To extract a rar file, e.g. file.rar:

> unrar e file.rar

To pack a folder, e.g. myFolder, into a rar file, e.g. file.rar:

> rar a file.rar myFolder

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
