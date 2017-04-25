# Code Quest Grader
**Python Script for grading and testing solutions to Code Quest problems.**
*NOTE* Only compatible with Python solution files. Uses Python 3.

## How it works
Code Quest problems follow a specific naming convention, namely:
* Files containing input are named: **Prob(problem number).in.txt**
* Files containing expected out are named: **Prob(problem number).out.txt**
so if the solution files are named in the same mannor we get a directory that looks like this:
```
Prob01.in.txt
Prob01.out.txt
Prob01.py
Prob02.in.txt
Prob02.out.txt
Prob02.py
...
```
`test_cq.py` looks for these files using the regular expression `Prob[0-9]{2}\.((in|out)\.txt|py)` and for each problem that has a corresponding input, output and solution file (known as a *problem set*), a test method is created and added to an empty test class. These in memory tests are then run using python's [unittest](https://docs.python.org/3/library/unittest.html). If a test fails, then the output from the failed test is written to `Prob01.error.txt`.

## Usage
By default, `test_cq.py` will find all problem sets in the working directory and test them. Just run: `python test_cq.py`.

To specify the directory containing problem sets, use the -d/--target_dir argument:
```
python test_cq.py -d ~/cq_probs
```

To specify specific problem numbers to omit, use the -o/--omit argument (separating each problem with a space):
```
python test_cq.py -o 1 2 3 4
```

To print out info log messages (level 20), use the -v/--verbose argument:
```
python test_cq.py -v
```

To set the logging level, use the -l/--logging-level argument. Does nothing if not used in conjunction with -v. Must be given a numeric log level corresponding to the log levels specified by Python's [logging documentation](https://docs.python.org/2/library/logging.html#levels):
```
python test_cq.py -l 10 -v
```

## License
Copyright 2017 Ryan Drew

Permission is hereby granted, free of charge, to any person obtaining a
copy of this software and associated documentation files (the "Software"),
to deal in the Software without restriction, including without limitation
the rights to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE
OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
