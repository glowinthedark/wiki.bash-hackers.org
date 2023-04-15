The one of the simplest way to check your bash/sh scripts is run it and check it output or run it and check the result. This tutorial shows how-to use [[https://github.com/pahaz/bashtest|bashtest]] tool for testing your scripts.

==== Write simple util ====

We have a simple **stat.sh** script:

&lt;code&gt;
#!/usr/bin/env bash

if [ -z &quot;$1&quot; ]
then
    DIR=./
else
    DIR=$1
fi

echo &quot;Evaluate *.py statistics&quot;
FILES=$(find $DIR -name '*.py' | wc -l)
LINES=$((find $DIR -name '*.py' -print0 | xargs -0 cat) | wc -l)
echo &quot;PYTHON FILES: $FILES&quot;
echo &quot;PYTHON LINES: $LINES&quot;
&lt;/code&gt;

This script evaluate the number of python files and the number of python code lines in the files.
We can use it like **./stat.sh &lt;dir&gt;**

==== Create testsuit ====

Then make test suits for **stat.sh**. We make a directory **testsuit** which contain test python files.

**testsuit/main.py**
&lt;code&gt;
import foo
print(foo)
&lt;/code&gt;

**testsuit/foo.py**
&lt;code&gt;
BAR = 1
BUZ = BAR + 2
&lt;/code&gt;

Ok! Our test suit is ready! 
We have 2 python files which contains 4 lines of code.

==== Write bashtests ====

Lets write tests. We just write a shell command for testing our work.

Create file **tests.bashtest**:

&lt;code&gt;
$ ./stat.sh testsuit/
Evaluate *.py statistics
PYTHON FILES:        2
PYTHON LINES:        4

&lt;/code&gt;

This is our test! This is simple. Try to run it.

&lt;code&gt;
# install bashtest if required!
$ pip install bashtest
&lt;/code&gt;

&lt;code&gt;
# run tests
$ bashtest *.bashtest
1 items passed all tests:
   1 tests in tests.bashtest
1 tests in 1 items.
1 passed and 0 failed.
Test passed.
&lt;/code&gt;

Thats all. We wrote one test. You can write more tests if you want.

&lt;code&gt;
$ ls testsuit/
foo.py  main.py

$ ./stat.sh testsuit/
Evaluate *.py statistics
PYTHON FILES:        2
PYTHON LINES:        4

&lt;/code&gt;

And run tests again:

&lt;code&gt;
$ bashtest *.bashtest
1 items passed all tests:
   2 tests in tests.bashtest
2 tests in 1 items.
2 passed and 0 failed.
Test passed.
&lt;/code&gt;

You can find more **.bashtest** examples in the [[https://github.com/pahaz/bashtest | bashtest github repo]]. You can also write your question or report a bug [[https://github.com/pahaz/bashtest/issues | here]].

Happy testing!