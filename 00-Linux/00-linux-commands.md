#### AWK 
The `awk` command is a powerful tool for pattern scanning and processing in Unix/Linux environments. It is commonly used for text processing and data extraction. Here are a few examples of how `awk` can be used:

### Basic Syntax

The basic syntax of the `awk` command is:

```sh
awk 'pattern { action }' file
```

### Examples

1. **Print the whole file:**

```sh
awk '{ print }' file.txt
```

This command prints every line of the file `file.txt`.

2. **Print specific columns:**

Assuming `file.txt` is a space-separated file, to print the first and third columns:

```sh
awk '{ print $1, $3 }' file.txt
```

3. **Print lines that match a pattern:**

To print lines containing the word "error":

```sh
awk '/error/ { print }' file.txt
```

4. **Sum a column of numbers:**

Assuming the second column contains numbers and you want to sum them up:

```sh
awk '{ sum += $2 } END { print sum }' file.txt
```

5. **Print lines with more than a certain number of fields:**

To print lines with more than 3 fields:

```sh
awk 'NF > 3' file.txt
```

6. **Field separator:**

If the file is comma-separated (CSV), specify the field separator with `-F`:

```sh
awk -F',' '{ print $1, $2 }' file.csv
```

7. **Conditional processing:**

To print the second column where the first column is greater than 100:

```sh
awk '$1 > 100 { print $2 }' file.txt
```

8. **Using `BEGIN` and `END` blocks:**

To print a header and footer:

```sh
awk 'BEGIN { print "Start" } { print } END { print "End" }' file.txt
```

### Complex Example

Suppose you have a CSV file `data.csv` with the following content:

```csv
Name,Math,Science,English
Alice,85,90,88
Bob,78,76,92
Carol,94,88,85
```

You can use `awk` to calculate the average score for each student:

```sh
awk -F',' 'NR > 1 { avg = ($2 + $3 + $4) / 3; print $1, avg }' data.csv
```

This command skips the first line (`NR > 1`), calculates the average of the scores in columns 2, 3, and 4, and prints the student's name along with their average score.

### Explanation

- `-F','`: Sets the field separator to a comma.
- `NR > 1`: Skips the first line (header).
- `avg = ($2 + $3 + $4) / 3`: Calculates the average score.
- `print $1, avg`: Prints the name and the average score.

These examples illustrate the versatility and power of the `awk` command for various text processing tasks.

### CUT
The `cut` command in Linux is used to extract sections from each line of input, usually from a file or the output of another command. Here are some common examples of how to use the `cut` command:

### Example 1: Cutting by Character
To extract specific characters from a line, use the `-c` option.

```bash
echo "Hello, World!" | cut -c 1-5
```
This command outputs:
```
Hello
```
It extracts characters 1 through 5 from the input string.

### Example 2: Cutting by Field
To extract specific fields from a line, use the `-f` option with a delimiter specified by the `-d` option. This is useful for CSV or similar files.

Assume we have a file `data.txt` with the following content:
```
apple,banana,cherry
dog,elephant,fox
grape,hippo,iguana
```

To extract the second field from each line:
```bash
cut -d ',' -f 2 data.txt
```
This command outputs:
```
banana
elephant
hippo
```

### Example 3: Cutting Multiple Fields
You can extract multiple fields by specifying them with a comma or a range.

```bash
cut -d ',' -f 1,3 data.txt
```
This command outputs:
```
apple,cherry
dog,fox
grape,iguana
```

### Example 4: Cutting by Byte Position
To extract specific bytes, use the `-b` option.

```bash
echo "Hello, World!" | cut -b 1-5
```
This command outputs:
```
Hello
```
It extracts bytes 1 through 5 from the input string.

### Example 5: Combining Cut with Other Commands
You can use `cut` in combination with other commands using a pipeline.

For example, to list all files in the current directory and display only the file permissions:
```bash
ls -l | cut -c 1-10
```
This command outputs something like:
```
drwxr-xr-x
-rw-r--r--
-rw-r--r--
```

These examples show how versatile the `cut` command can be for extracting specific portions of text from input.

###  archiving and compressing files
Compressing files with gzip

gzip is program used to compress files in Linux, they end in a .gz extension.

To compress a file down:

``` gzip mycoolfile```
To decompress the file:

```gunzip mycoolfile.gz```

Creating archives with tar
Unfortunately, gzip can't add multiple files into one archive for us. Luckily we have the tar program which does. When you create an archive using tar, it will have a .tar extension.


``` tar cvf mytarfile.tar mycoolfile1 mycoolfile2 ```
- c - create
- v - tell the program to be verbose and let us see what it's doing
- f - the filename of the tar file has to come after this option, if you are creating a tar file you'll have to come up with a name

***Unpacking archives with tar***

To extract the contents of a tar file, use:

```tar xvf mytarfile.tar```

- x - extract
- v - tell the program to be verbose and let us see what it's doing
- f - the file you want to extract