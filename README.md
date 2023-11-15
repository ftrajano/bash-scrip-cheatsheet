# bash-scrip-cheatsheet
## Arrays

### Creating an array in Bash
1. Declare without adding elements
   ```shell
   declare -a my_first_array
   ```
2. Create and add at the same time
   ```shell
   my_first_array=(1 2 3) # remember: No commas!
   ```

### Important array properties
* All array elemnts can be return using ```array[@]```. though do note, Bash requires curly
brackets around the array name when you want to access these properties
```shell
my_array=(1 3 5 2)
echo ${my_array[@]}
>> 1 3 5 2
```
* The length of an array is accessed using ```#array[@]```
```shell
${#my_array[@]}
```

### Manipulating array elements
* accessing array elements using square brackets.
```shell
my_first_array=(15 20 300 42)
echo ${my_first_array[2]}
>> 300
```

* Set array elements using the index notation.
```shell
my_first_array=(15 20 300 42 23 2 4 33 54 67 66)
my_first_array[0]=999
echo ${my_first_array[0]}
>>999
```
* Use the notation ```array[@]:N:M``` to "slice" out a subset of the array.
```shell
my_first_array=(15 20 300 42 23 2 4 33 54 67 66)
echo ${my_first_array[0]:3:2}
>>42 23
```

* Append to an array using ```array+=(elements)```
```shell
my_first_array=(15 20 300 42 23 2 4 33 54 67 66)
my_first_array+=(10) # if you forget the parenthesis a 10 will be concatenated to the first element
```

## Associative arrays
Similar to Python dictionaries
### Creating an associative array
You can only create an associative array using the declare syntax (and uppercase -A).
You can either declare first, then add elements or do it all on one line.
e.g.
```shell
declare -A city_details # Declare first
city_details=([city_name]="New York" [population]=14000000) # Add elements
echo {city_details[city_name]} # Index using key to return a value
>> New York
```

```shell
declare -A city_details=([city_name]="New York" [population]=14000000)
```

You can access the keys of an associative array with an ```!```
```shel
echo ${!city_details[@]} # return all the keys
>> city_name population
```
