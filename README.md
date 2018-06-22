
# Table of Contents
1. [Understanding the challenge](README.md#understanding-the-challenge)
2. [Implementation details](README.md#implementation-details)
3. [Test Results](README.md#test-results)
4. [My input files](README.md#my-input-files)
5. [My output file](README.md#my-output-file)

# Understanding the challenge


# Implementation details

None


# Test Results


# My input files

From the website SEC weblogs I can access to a lot of datasets:
I picked three sample datasets at one day in 2003, 2011, 2017.

## sessionization.py to sessionization_opt.py

    From the details of challange I know the duration is a important value to check if an IP is in a session of a single web page document request. The value will range from 1 to 86,400 (i.e., one second to 24 hours)
    In the given test example, the duration time is 2 seconds. By increasing the duration time : 2 seconds , 3seconds and 100 seconds, the computing time of output file increased also. 
    With a large dataset in 2017, which size is 2.78GB, the computating time is as long as more than 20 mins in the first version of my sessionization.py. It is too long to be a applicable program. So I made changes like following:
    
    real	6m3.742s
    user	6m0.968s
    sys	0m1.282s

    real	3m17.475s
    user	3m15.101s
    sys	0m1.084s



