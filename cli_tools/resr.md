* A search and replace utility written with python:

https://github.com/eliranwong/bible-verse-parser/blob/master/RegexSearch.py

This script supports:<br>
* regular expression
* searching multiple lines, which "sed" does not support
* search with back references, which "awk" does not support
* option to use literal strings for search and replace
* option to overwrite the original file(s)
* work on multiple files or folders in one go
* perform multiple search and replace in one go
* two modes of searching, simple & deep, for power users
* power users can customise the script by editing function "processInputText"
* can handle large-sized file(s)
* etc.

Usage:<br>

RegexSearch.py [optional --deep]

OR:

RegexSearch.py [a nested tuple of search & replace items] [optional --overwrite] [file1 / folder1] [file2 / folder2] [file3 / folder3] ...<br>
Support multple files / folders, starting from the second parameter.<br>

To make this script executable, run, e.g.:<br>
> chmod +x RegexSearch.py<br>

To provide a nested tuple / list of search & replace items on command line, e.g.:<br>
> ./RegexSearch.py '(("test", "TEST"), ("[a-e]", r"x\\1x"))' --overwrite test1.txt test2.txt<br>

e.g. Convert two json files to a tab-separated text:<br>
> RegexSearch.py '(("{\"bNo\": ([0-9]+?), \"cNo\": ([0-9]+?), \"vNo\": ([0-9]+?), \"vText\": \"(.*?)\"},", r"\1\t\2\t\3\t\4"),)' ULT.json UST.json

To work with dynamic scripting, edit the content of function "processInputText" and run, e.g.:<br>
> ./RegexSearch.py '()' test.txt test1.txt<br>

The first parameter is optional to work on a single file or a single folder.  This assumes power users edit the content of function "processInputText" according to their own needs, e.g.:<br>
> ./RegexSearch.py test.txt<br>

To run with interactive mode, simple run:<br>
> ./RegexSearch.py

# Interactive mode

Below are some examples of "interactive mode":

In the following examples, we copy the scrip and put in folder "~/bin":

> cp RegexSearch.py ~/bin/resr<br>
> chmod +x ~/bin/resr

# Example: Simple search & replace:

<img src="resr_example_2a.png" />

<img src="resr_example_2b.png" />

# Examples - Use String Literals

* Use string literals to search multiple lines and replace with back references:

<img src="resr_example_1.png">

* Another example of using string literals:

<img src="resr_eg_literal_string.png" />

# Example: Enable Deep Mode

<img src="resr_example_deep_mode.png" />

* To use as an import to build others, for example:<br>
https://github.com/eliranwong/bible-verse-parser/blob/master/BibleVerseParser.py
