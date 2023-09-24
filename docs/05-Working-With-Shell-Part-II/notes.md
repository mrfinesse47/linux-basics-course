## io redirection

### redirecting standard output

> echo $SHELL > shell.txt - writes ansd replaces

- use >> to append

#### redirect stderr

> cat missing_file 2> error.txt

- to append 2>>

#### to silence errors

> cat missing_file 2> /dev/null - they call dev/null the bitbucket

#### pipes

- tee

echo $SHELL | tee shell.txt : same as > ?

caleston123
