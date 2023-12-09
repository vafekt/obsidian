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



