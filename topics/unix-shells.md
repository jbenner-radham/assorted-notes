Unix Shells
===========

POSIX Shell
-----------

- Remove a prefix from a variable ('v' in this case): `{LATEST_RELEASE#v}`
- Remove a suffix from a variable ('/' in this case): `${TMPDIR%/}`
- Unset a function: `unset -f $FUNCTION_NAME`

Z Shell (zsh)
-------------

- Append to `$PATH:`: `path+=("${$HOME}/.local/bin")`
- Prepend to `$PATH`: `path=("${$HOME}/.local/bin" $path)`
- Check if a path is in `$PATH`: `(( $path[(Ie)$HOME/.local/bin] ))`
- Delete the whole line: <kbd>Ctrl</kbd> + <kbd>U</kbd>
- Display the attributes and value of all declared variables: `typeset -p`
- Get a variable type via a parameter expansion flag (`man zshexpn`): `echo "${(t)VARIABLE_NAME}"`
- Remove duplicates in `$PATH`: `typeset -aU path`
- Unset a function: `unfunction $FUNCTION_NAME`
- View the manpage for the built-ins: `man zshbuiltins`
- View the options manpage: `man zshoptions`
