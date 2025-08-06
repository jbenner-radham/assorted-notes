Unix Shells
===========

POSIX Shell
-----------

- Unset a function: `unset -f $FUNCTION_NAME`

Z Shell (zsh)
-------------

- Delete the whole line: <kbd>Ctrl</kbd> + <kbd>U</kbd>
- Display the attributes and value of all declared variables: `typeset -p`
- Get a variable type via a parameter expansion flag (`man zshexpn`): `echo "${(t)VARIABLE_NAME}"`
- Remove duplicates in `$PATH`: `typeset -aU path`
- Unset a function: `unfunction $FUNCTION_NAME`
- View the manpage for the built-ins: `man zshbuiltins`
- View the options manpage: `man zshoptions`
