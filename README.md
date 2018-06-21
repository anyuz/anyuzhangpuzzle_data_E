
# Table of Contents
1. [Understanding the challenge](README.md#understanding-the-challenge
2. [Implementation details](README.md#implementation-details)
3. [Test Results](README.md#test-results)
4. [My input files](README.md#my-input-files)
5. [My output file](README.md#my-output-file)

# Understanding the challenge


# Implementation details

# Test Results

# My input files

### `log.csv`

The SEC provides weblogs stretching back years and is [regularly updated, although with a six month delay](https://www.sec.gov/dera/data/edgar-log-file-data-set.html). 

For the purposes of this challenge, you can assume that the data is being streamed into your program in the same order that it appears in the file with the first line (after the header) being the first request and the last line being the latest. You also can assume the data is listed in chronological order for the purposes of this challenge.

While you're welcome to run your program using a subset of the data files found at the SEC's website, you should not assume that we'll be testing your program on any of those data files.

Also, while we won't expect your program to be able to process all of the SEC's weblogs (there is over 1TB of data), you should be prepared to talk about how you might design or redesign your program should the challenge be changed to require you to process hundreds of gigabytes or even a terabyte.

For the purposes of this challenge, below are the data fields you'll want to pay attention to from the SEC weblogs:

* `ip`: identifies the IP address of the device requesting the data. While the SEC anonymizes the last three digits, it uses a consistent formula that allows you to assume that any two `ip` fields with the duplicate values are referring to the same IP address
* `date`: date of the request (yyyy-mm-dd) 
* `time`:  time of the request (hh:mm:ss)
* `cik`: SEC Central Index Key
* `accession`: SEC document accession number
* `extention`: Value that helps determine the document being requested

There are other fields that can be found in the weblogs. For the purposes of this challenge, your program can ignore those other fields.

Unlike other weblogs that contain the actual http web request, the SEC's files use a different but deterministic convention. For the purposes of this challenge, you can assume the combination of `cik`, `accession` and `extention` fields uniquely identifies a single web page document request. Don't assume any particular format for any of those three fields (e.g., the fields can consist of numbers, letters, hyphens, periods and other characters)

The first line of `log.csv` will be a header denoting the names of the fields in each web request. Each field is separated by a comma. Your program should only use this header to determine the order in which the fields will appear in the rest of the other lines in the same file.

### `inactivity_period.txt`
This file will hold a single integer value denoting the period of inactivity (in seconds) that your program should use to identify a user session. The value will range from 1 to 86,400 (i.e., one second to 24 hours)

# My output file

Once your program identifies the start and end of a session, it should gather the following fields and write them out to a line in the output file, `sessionization.txt`. The fields on each line must be separated by a `,`:

* IP address of the user exactly as found in `log.csv`
* date and time of the first webpage request in the session (yyyy-mm-dd hh:mm:ss)
* date and time of the last webpage request in the session (yyyy-mm-dd hh:mm:ss)
* duration of the session in seconds
* count of webpage requests during the session

Unlike the input weblog data file and for the purposes of this challenge, your program should not write a header line to the output file but instead write just the results. Each line should have the fields in the exact order detailed above. Fields must be separated by a comma.

If your program is able to detect multiple user sessions ending at the same time, it should write the results to the `sessionization.txt` output file in the same order as the user's first request for that session appeared in the input `log.csv` file.

