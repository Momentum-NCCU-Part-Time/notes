# Working with files in Python

Python can interact with a file similarly to how a user would. Python first needs to open a file and then it can 
read it. The following example is for a txt file. To 
work with a CSV file, you would need a module called `csv`.

## The most typical pattern starts like this:
```py
# 'r' is for read only mode, 'w' would be for write
# 'yourfile.txt' should be the relative path to your file
with open('yourfile.txt', 'r') as f:
    # code to read and process the file goes here, where the file is referred to as f.
    # when the indented code block stops, Python will close the file, and f will no longer be defined
    # read() converts the file to a string
    file_string = f.read()
    # splitlines() will return a list with each element being a line in the file
    file_list = file_string.splitlines()
    # strip() and split() can also be helpful in this process.

# this will print out one line at a time
for line in file_list:   
    print(line)
```
