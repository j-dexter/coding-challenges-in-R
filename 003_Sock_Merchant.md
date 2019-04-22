## CHALLENGE 003: Find matching pairs of socks

# The Sock Merchant challenge from HackerRank

## Instructions:

John works at a clothing store. He has a large pile of socks that he must pair by color for sale. Given an array of integers representing the color of each sock, determine how many pairs of socks with matching colors there are.

For example, there are  socks with colors . There is one pair of color  and one of color . There are three odd socks left, one of each color. The number of pairs is .

Function Description

Complete the sockMerchant function in the editor below. It must return an integer representing the number of matching pairs of socks that are available.

sockMerchant has the following parameter(s):

n: the number of socks in the pile
ar: the colors of each sock
Input Format

The first line contains an integer , the number of socks represented in . 
The second line contains  space-separated integers describing the colors  of the socks in the pile.

Constraints

 where 
Output Format

Return the total number of matching pairs of socks that John can sell.

Sample Input

9
10 20 20 10 10 30 50 10 20
Sample Output

3

## My Solution

    # Enter your code here. Read input from STDIN. Print output to STDOUT

    # Load library
    library(dplyr)

    # Get input data
    input <- file('stdin', open = 'r')

    # Get n from first line 1
    n <- readLines(input, n=1)

    # Get data from line 2
    ar_raw <- suppressWarnings(readLines(input, n=2));

    # Split into individual strings
    ar_split <- strsplit(ar_raw, " ")

    # String to integer conversion
    ar <- as.numeric(unlist(ar_split))

    # Function to get count of sock-pairs
    sockMerchant <- function(n, ar) {

        # Put vector into table
        ar_tbl <- tibble(ar)

        # Groupby sock-type and get sock-pair count per type
        ar_grp_tbl <- group_by(ar_tbl, ar)
        ar_agg_tbl <- summarize(ar_grp_tbl,
                                n_type = n(),
                                n_pairs = floor( n_type / 2))

        # Count total sock-pairs
        num_sock_pairs <- sum(ar_agg_tbl$n_pairs)

        return(num_sock_pairs) 
    }

    # Use function to get answer
    answer <- sockMerchant(n, ar)

    # Display answer
    write.table(as.numeric(answer[1]), append=T, row.names = F, col.names = F)
