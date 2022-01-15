## Expected results of reimplementing pipes and redirections in bash

Suppose we have a file test.txt:
```
I am a testfile
```
### `<` redirects to stdin

And we redirect it to cat -e:

```
< test.txt cat -e
```

we expect:

```
I am a testfile$
```

From the `$` we can see the file actually passed through `cat -e`, instead of going directly to stdout for example.

### Redirections can be placed anywhere

These all give the same results
```
< test.txt cat -e
cat < test.txt -e
cat -e < test.txt
```
### You can have multiple redirections, they are processed in order

Suppose we have a second file test2.txt:
```
This is the second testfile
```

and we redirect both files to stdin:
```
< test.txt < test2.txt cat -e
```

Then even though test.txt is first redirected to stdin, test2.txt is overrides it, so you get:
```
This is the second testfile$
```
