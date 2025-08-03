Unix Shells
===========

POSIX Shell
-----------

- Unset a function: `unset -f $FUNCTION_NAME`

Z Shell (zsh)
-------------

- Display the attributes and value of all declared variables: `typeset -p`
- Get a variable type via a parameter expansion flag (`man zshexpn`): `echo "${(t)VARIABLE_NAME}"`
- Unset a function: `unfunction $FUNCTION_NAME`
