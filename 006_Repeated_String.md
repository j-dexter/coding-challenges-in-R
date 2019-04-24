## CHALLENGE 006: Repeated String (HackerRank)

This challenge is from the Interview Preparation, KitWarm-up Challenges

## INSTRUCTIONS (from HackerRank)

Lilah has a string, , of lowercase English letters that she repeated infinitely many times.

Given an integer, , find and print the number of letter a's in the first  letters of Lilah's infinite string.

For example, if the string  and , the substring we consider is , the first  characters of her infinite string. There are  occurrences of a in the substring.

### Function Description

Complete the repeatedString function in the editor below. It should return an integer representing the number of occurrences of a in the prefix of length  in the infinitely repeating string.

repeatedString has the following parameter(s):

s: a string to repeat
n: the number of characters to consider

### Input Format

The first line contains a single string, . 
The second line contains an integer, .

### Constraints

For  of the test cases, .

### Output Format

Print a single integer denoting the number of letter a's in the first  letters of the infinite string created by repeating  infinitely many times.

### Sample Input 0

    aba
    10

### Sample Output 0

    7

Explanation 0 
The first  letters of the infinite string are abaabaabaa. Because there are  a's, we print  on a new line.

### Sample Input 1

    a
    1000000000000

### Sample Output 1

    1000000000000

Explanation 1 
Because all of the first  letters of the infinite string are a, we print  on a new line.


## MY SOLUTION

    input <- suppressmessages(readLines("stdin"))
    s <- input[1]
    n <- as.numeric(input[2])

    # Load libraries
    library(stringr)
    library(dplyr)
    options(scipen=999) # Avoids scientific notation

    # Set counter
    count_a <- 0

    repeatedString <- function(s, n) {

        if (str_count(s, pattern = "a") == 0) {
            final_count_a <- count_a
            message("In repeatedString(): Input string has no letter 'a' present.")
        } else {

            # Get count of characters in string
            chr_in_str <- nchar(s)

            # Get count (as int) of how many time the 'whole' string will be repeated
            s_into_n <- floor(n / chr_in_str)

            # Use remainder to subset leftover beginning of string
            s_remainder <- n%%chr_in_str
            s_subset    <- str_sub(string = s, start = 1, end = s_remainder)

            # Get count of 'a' in base string
            a_in_base_s <- str_count(s, pattern = "a") 

            # Get count of 'a' in remainder string
            a_in_remainder <- str_count(s_subset, pattern = "a")

            # Count number of a's in the first 'n' letters of 's'
            final_count_a <- a_in_base_s * s_into_n + a_in_remainder

        }

        return(final_count_a)

    }

    final_count_a <- repeatedString(s, n)
    ##print(final_count_a)

    write.table(final_count_a, row.names = F, col.names = F)

## END SOLUTION
