# KdTree-StarterCode

This repository contains the starter code for the k-d tree assignment in COL362/632 (Intro. to Database Management Systems) being held at IIT Delhi.

The part (d) of the assignment is a competition among all the students based on the time taken by their k-d tree implementation to answer a kNN-query.
 
## Program Structure

The file **parent.py** is provided to you. It is the program that will time your submission. You are expected to submit your code along with a **run.sh** which compiles and runs your program (Specifications below).

In order for parent.py to measure the time taken by your program to just answer the query (excluding the k-d tree construction time), the following mechanism has been adopted.

 1. parent.py will execute `sh run.sh <dataset_file>` as a child process. (run.sh should in turn compile and run your program) (Here <**dataset_file**> is the name of the file containing the data points - Format specified below) 
 2. Your program (child) should construct the k-d tree using <dataset_file> and output "0" on the standard output (stdout) when done. This would be read by the parent.
 3. parent.py would then write the name/path of the **<query_file>** (which contains the query point for kNN - Format specified below) and the value of **k** on your standard input (stdin). It also starts the timer now.
 4. Your program should now read the name of the <query_file> and the value of k from stdin and process the query using the k-d tree. The output (the k nearest neighbors) should then be written to **results.txt**. (Format specified below)
 5. Your program should then output "1" on stdout so that the parent can stop the timer and check your results.txt.

Sample run.sh and sample.cpp (and a sample.py, in case you wish to work in Python) have been provided to demonstrate how to communicate with parent.py. Feel free to extend them as you need.

## File Formats

 - A point is represented as a space separated list of values along each dimension.
 Eg. 1.2 4.3 represents a 2-dimensional point.
 - Each line in **<dataset_file>** and **results.txt** should contain a point each. <**query_file**> contains a single line (point) in the same format. 
 
 Example: Suppose the points are 2-dimensional and <dataset_file> contains 3 points, it would look something like
0.0 1.0
1.0 0.0
0.0 0.0
Now if the <query_file> is:
1.0 1.0
Then for k = 2, results.txt should look like:
0.0 1.0
1.0 0.0

**NOTE**: The results.txt file **must** be sorted in ascending order of distance to the query point. For a tie-breaker (2 points equi-distant from query point), use lexicographical ordering between the 2 points i.e. if two d-dimensional points A and B are equi-distant from the query point, then A < B if for some 0$\leq$m$\lt$d,  A[m] < B[m] and A[i]=B[i] for 0$\leq$i$\lt$m. (where A[i] represents value of A along i-th dimension) (Eg. [1.0 2.0] < [1.0 3.0])

**NOTE**: The stdout and stdin of your program are used for communication with the parent.py. Hence, for any debugging purposes, do not print anything on stdout, instead use stderr (using cerr in C++ for example).

## Command to run

    python parent.py <dataset_file> <query_file> <k>
parent.py is compatible with Python 2 and 3 and with both linux and windows. For any issues, feel free to contact:
Abhishek Gupta <abhi19gupta@gmail.com>