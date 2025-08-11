Unix Shells
===========

POSIX Shell
-----------

### Remove A Prefix From A Variable

```shell
VERSION="v1.0.0"
UNPREFIXED_VERSION="${VERSION#v}"

printf '%s\n' "${UNPREFIXED_VERSION}"
# >>> 1.0.0
```

### Remove a Suffix From a Variable

```shell
URL="https://www.example.com/"
URL_WITHOUT_TRAILING_SLASH="${URL%/}"

printf '%\n' "${URL_WITHOUT_TRAILING_SLASH}"
# >>> https://www.example.com
```

### Transform Uppercase Text to Lowercase

```shell
echo 'HELLO WORLD!' | tr '[:upper:]' '[:lower:]'
# >>> hello world!
```

### Unset a Function

```shell
function example {
  printf 'Hello world!\n'
}

example
# >>> Hello world!

unset -f example

example
# >>> sh: example: command not found
```

Z Shell (zsh)
-------------

### Append to `$PATH`

```shell
print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin

path+=("/path/to/bin")

print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin:/path/to/bin
```

### Prepend to `$PATH`

```shell
print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin

path=("/path/to/bin" $path)

print "${PATH}"
# >>> /path/to/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

### Check if a Path Is in `$PATH`

```shell
path+=("/path/to/bin")

(( $path[(Ie)/path/to/bin] )) && print 'Found in path!'
# >>> Found in path!
```

### Delete the Whole Line in a Shell Session

<kbd>Ctrl</kbd> + <kbd>U</kbd>

### Display the Attributes and Values of All Declared Variables

```shell
typeset -p
# >>> typeset 0=-zsh
# >>> typeset BOLD=$'\C-[[1m'
# >>> typeset BUFFER=''
# >>> ...
```

### Get a Variable Type via a Parameter Expansion Flag

```shell
local example="Hello world!"

print "${(t)example}"
# >>> scalar
```

### Remove Duplicates in `$PATH`

```shell
print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin

path+=("/path/to/bin")

print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin:/path/to/bin

path+=("/path/to/bin")

print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin:/path/to/bin:/path/to/bin

typeset -aU path

print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin:/path/to/bin
```

### Split a String Using a Parameter Expansion Flag

```sh
print "${PATH}"
# >>> /usr/bin:/bin:/usr/sbin:/sbin

print -l "${(s[:])PATH}"
# >>> /usr/bin
# >>> /bin
# >>> /usr/sbin
# >>> /sbin
```

### Unset a Function

```shell
function example() {
  print 'Hello world!'
}

example
# >>> Hello world!

unfunction example

example
# >>> zsh: command not found: example
```

### View the Manpage for Built-Ins

```shell
man zshbuiltins
```

### View the Manpage for Expansion and Substitution

```shell
man zshexpn
```

### View the Options Manpage

```shell
man zshoptions
```
