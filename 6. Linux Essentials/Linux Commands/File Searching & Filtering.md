|Command|Description|
|---|---|
|`find / -name "file.txt"`|Searches for a file named file.txt from root|
|`find . -name "*.pdf"`|Searches for PDF files in current directory|
|`find / -type f -name "file*"`|Finds files starting with "file"|
|`find / -type d -name "x.gz"`|Finds directories named "x.gz"|
|`find / -name "x.gz"|grep nagyan`|
|`find / -name "x.gz"|grep nagyan > /dev/null`|
|`locate file.txt`|Quickly finds file using locate database|
|`updatedb`|Updates the `locate` database|
|`grep "main" file.c`|Searches for “main” inside file.c|
|`grep -r "password" /etc`|Recursive search for "password" in `/etc`|
|`grep -n "root" /etc/passwd`|Finds "root" in `/etc/passwd` with line numbers|