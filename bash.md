# Bash

## Useful links

https://medium.com/@robaboukhalil/the-weird-wondrous-world-of-bash-arrays-a86e5adf2c69
https://stackoverflow.com/questions/2188199/how-to-use-double-or-single-brackets-parentheses-curly-braces

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

