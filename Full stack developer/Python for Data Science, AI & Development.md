**Types**
- Integer: int
- Float: float
- String: str
- Boolean: True or False
- 0 is integer type
You can convert type to type (for example, from integer to float. But from float to int will be floor rounding). You can also convert string to int.

Expression and variables

**String**
my_name = “BobbyTarantino” 
print (my_name[::1]) #BobbyTarantino 
print (my_name[::-1 ]) #onitnaraTybboB 
print (my_name[::2]) #Bbyaatn 
print (my_name[::-2]) #oinrTbo

3 * "hello" == hellohellohello

Escape sequences: "\" (for example, \n or \t)

**List and tuples**
Tuples are an ordered sequence, recognized as brackets (1, 2, 3, 4, 5)
- Tuples can store any data types such as string, integer, float...
- tuples[-1] = 5
- Tuples (also list) can concatenate, which means: tuple2 = tuple1 + ("haha", 10)
- They also have slicing attributes
- But tuples are immutable
List is mutable, order sequence.
- Difference between extend and append.
![[Pasted image 20231209200029.png]]
![[Pasted image 20231209200052.png]]

**Dictionary**
Is a type of collection in Python. It has key and value with curly brackets {}
The keys have to be immutable and unique
The values can be immutable, mutable and duplicates

**Sets**
Type of collections
It is unordered (does not record element position)
Only has unique elements
Defined as {}. For example: set = {1, 2, 3, 4}
We can convert list to set by using set(list)
Set operation:
- Adding item: set.add("hello")
- Removing item: set.remove("bye")
We can use mathematical operation for two sets to return False or True, also to return new set
![[Pasted image 20231209201758.png]]
![[Pasted image 20231209201838.png]]
![[Pasted image 20231209201911.png]]

**Exception Handling**
It is Try...Except statement
It can be one try with more than one except:
![[Pasted image 20231209230849.png]]

It can be useful when using else for successful input
![[Pasted image 20231209230952.png]]

We can you the final statement to do the final process after all
![[Pasted image 20231209231111.png]]

**Objects and Classes**
Each object has:
- A type
- An internal data representation (blueprint)
- A set of procedures for interacting with object (methods)
	- Sorting is an example of a method that interacts with the data in the object
An object is an instance of a particular type
![[Pasted image 20231209233648.png]]
Creating the class. Then we can get objects or instances of that class
- Data attributes
	- We use constructor __init__(self,...) to initialize data attributes
- Methods
![[Pasted image 20231209234153.png]]

**Reading and Writing Files with Open**
First we need to open files using open()```
with open('data.txt', 'r') as f:
    data = f.read()```
- open() takes a filename and a mode as its arguments (in this case, it is read only mode). To write data to a file, we use w instead:```
with open('data.txt', 'w') as f:
    data = 'some data to be written to the file'
    f.write(data)```
- In the case for reading, if the file does not exist, it will be error. But in the case for writing, it will automatically create a new file.
For listing the names of files and subdirectories in the specified directory, we use os library```
import os
entries = os.listdir('my_directory/')```
- Now entries is the list containing files and subdirectories. We can use for loop to enumerate all items
- We can use scandir instead of listdir, but it returns iterator instead of list. For showing the files and directories, we need to use entry.name in for loop:```
with os.scandir('my_directory/') as entries:
    for entry in entries:
        print(entry.name)```
- We can also use another library (pathlib), which can show both names and attributes of files```
from pathlib import Path
entries = Path('my_directory/')
for entry in entries.iterdir():
    print(entry.name)```
- In os library, there is a method for checking if this is a directory:```
basepath = 'my_directory/'
with os.scandir(basepath) as entries:
    for entry in entries:
        if entry.is_dir():
            print(entry.name)```
- For getting file attributes in os library, we use entry.stat() in the for loop
Making directories
- Creating a single directory```
os.mkdir('example_directory/')``````

from pathlib import Path
p = Path('example_directory/')
try:
	p.mkdir()
except FileExistsError as err:
	print(err)```
- Creating multiple directories (1 directory with multiple subdirectories)```
os.makedirs('2018/10/05')```
	- We can even set the mode for the file```
os.makedirs('2018/10/05', mode=0o770)```

After using, please remember to close the file: file1.closed, but the with statement automatically close the file object
We can read every line by using file.readlines()

**Pandas**
Pandas is a popular library for data analysis
![[Pasted image 20231210161723.png]]
We can use import pandas as pd for short terminology
![[Pasted image 20231210161902.png]]
Now we have dataframes containing rows and columns. We often cast dictionary to dataframes.
![[Pasted image 20231210162200.png]]
![[Pasted image 20231210162255.png]]
You can see here we have two square brackets which return new dataframe. If we use one bracket, the result is the type of series
![[Pasted image 20231210162938.png]]
Saving file: df1.to_csv('new_song.csv')
`loc()` is a label-based data selecting method which means that we have to pass the name of the row or column that we want to select. This method includes the last element of the range passed in it.
Simple syntax for your understanding:
- loc[row_label, column_label]

`iloc()` is an indexed-based selecting method which means that we have to pass an integer index in the method to select a specific row/column. This method does not include the last element of the range passed in it.
Simple syntax for your understanding:
- iloc[row_index, column_index]

**Numpy**
It is a library for scientific computing. 
a=np.array([0,1,7,3, 7])
![[Pasted image 20231210165410.png]]
![[Pasted image 20231210165444.png]]
