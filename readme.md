*This readme will be replaced*

# Squash
A provably fast and expensive hash algorithm</br>

## Benchmarking
To test out squash, it is recommended to use the shipped python scripts which can be found in `tests/`. Please note that the C code in this folder writes to a file and therefore is a lot slower than the C code in squash.c.
### Parameters
Atleast one algorithm has to be tested, atleast one test option has to be specified. 
```
Algorithm options


Test options
-b, --bit                 Enable bit histogram
-B, --bucket              Enable bucket histogram
-c, --collisions          Enable collision testing
-i, --iterations number   Set the number of iterations
-t, --time                Enable runtime testing
Output options
-o, --out directory       Specify out directory
-P, --plot                Show plots instead of writing them
-w, --write               Write to a file instead of console outputs

-h, --help                Display this help message
```
By default the out directory is set to "results" and iterations are set to 65536 to enable quick, relatively accurate testing. All other values are disabled by default.</br>
An example for a command could be the following: `python3 tests.py -s -i 65536 -t -c -w -b -B`. It performs all tests on squash while using 65536 (2**16) iterations.</br>
**ATTENTION** Since the "similarity" test is obsolete and relies on eyeballing, it has been removed. To check the similarity of the hashes with similar inputs, go to docs/hash_sample.txt or generate one yourself using the python module in tests/.


### Dependencies
Those scripts use [Python3.7](https://www.python.org/downloads/release/python-372/), please make sure you use it instead of the older versions.
To create plots (bucket histogram and bit histogram), you will need to install [matplotlib](https://matplotlib.org/).
You can install it using the following command `python3.7 -m pip install matplotlib`.</br>
A CPU has to be capable of performing 64bit operations, speedups for the [AES-NI](https://en.wikipedia.org/wiki/AES_instruction_set) and ARMv8 are available.

### Plots
The plots have no labeling and therefore are described in here.</br> 
In the bit histogram you can see the average value of a group of four bits at a specific position. The Y-Axis shows the average value where the X-Axis displays the position. Ideally it is a straight line at the value of 8.</br>
The bucket histogram cuts of the first part of every hash value and only takes the last 16bit. Those are then used to fit everything into a bucket. The X-Axis displays the buckets, where each bucket corresponds to a value (such as 0, 1 or 65535). The Y-Axis corresponds to the absolute number of entities in this bucket. Ideally this is a straight line aswell at ITERATIONS/65536.</br>

**Please note, that this Project is still under development. It works perfectly fine on all machines machines**

If you have got any issues, please open a case.
If you know how to improve parts of the code, make sure to send a pull request.





