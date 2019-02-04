# Bash

## Useful links

https://medium.com/@robaboukhalil/the-weird-wondrous-world-of-bash-arrays-a86e5adf2c69
https://stackoverflow.com/questions/2188199/how-to-use-double-or-single-brackets-parentheses-curly-braces
https://www.tldp.org/LDP/abs/html/string-manipulation.html

## Colors

```shell
WHITE=$(tput setaf 7)
BLUE=$(tput setaf 6)
RED=$(tput setaf 9)
CLEAR=$(tput sgr0)
```

## Argument parsing

```shell
ARG1=defaultValue
for i in "$@"; do
	case $1 in
		--help | -? | -h)
			echo "$(basename "$0"): --arg1=value1"
			echo "    <tool description>"
			echo "    Options:"
			echo "        -h --help:         Show this help"
			echo "        --arg1=<value>:    Argument 1"
			exit 0
			;;
		--arg1)
			ARG1="$2"
			shift 2
			;;
		--arg1=*)
			ARG1="${i#*=}"
			shift
			;;
		*)
			echo "${RED}$(basename "$0"): Unknown option: $i. Pass --help to view the available options.${CLEAR}"
			exit 1
			;;
	esac
done
```

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