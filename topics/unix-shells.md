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
example() {
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

### Dynamically Source Files

```shell
# The parenthesized characters are called glob qualifiers and do the following:
#  .: Match only plain files.
#  N: Set the `NULL_GLOB` option for the current pattern. This will suppress the
#     error raised when no files match the current pattern.
#  r: Match only owner-readable files.
# See: https://zsh.sourceforge.io/Doc/Release/Expansion.html#Glob-Qualifiers
# Note: The glob won't work if it's quoted.
for file in $XDG_CONFIG_HOME/zsh/*.zsh(.Nr); do
  source "${file}"
done

# Unset the loop variable so it doesn't persist in the shell session.
unset file
```

### Get a Variable Type via a Parameter Expansion Flag

```shell
local example="Hello world!"

print "${(t)example}"
# >>> scalar
```

### Join an Array Into a String

```shell
local words=(foo bar baz)

print -l $words
# >>> foo
# >>> bar
# >>> baz

# Join on a space (" ").
print -l ${(j[ ])words}
# >>> foo bar baz

# Join on a colon (":").
print -l ${(j[:])words}
# >>> foo:bar:baz

local separator='=>'

# Using a separator variable.
print -l ${(pj[$separator])words}
# >>> foo=>bar=>baz

# Alternate separator variable syntax.
print -l ${(pj.$separator.)words}
# >>> foo=>bar=>baz
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

### Unquote a String

```shell
local example='"Hello world!"'

print "${example}"
# >>> "Hello world!"

print "${example:Q}"
# >>> Hello world!
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
