# Bash

## Useful links

https://medium.com/@robaboukhalil/the-weird-wondrous-world-of-bash-arrays-a86e5adf2c69
https://stackoverflow.com/questions/2188199/how-to-use-double-or-single-brackets-parentheses-curly-braces
https://www.tldp.org/LDP/abs/html/string-manipulation.html

## String manipulation

### Substring Removal

* Delete shortest match of $substring from front of $string: ${string#substring}
* Delete longest match of $substring from front of $string: ${string##substring}
* Delete shortest match of $substring from end of $string: ${string%substring}
* Delete longest match of $substring from end of $string: ${string%%substring}

## Arrays

### Create empty array

```shell
arr=()
```

### Calculate array size

```shell
$(#arr[@])
```

### Append value

```shell
arr+=(value)
```

### Iterate over each element (foreach)

```shell
for element in "${arr[@]}"; do
	# ...
done
```

### Iterate over each element by index

```shell
for index in "${!arr[@]}"; do
	printf "arr[%s]=%s" "$index" "${arr[$index]}"
done
```

### For each line in file

```shell
while IFS='' read -r line || [[ -n "$line" ]]; do
    echo "Text read from file: $line"
done < file
```