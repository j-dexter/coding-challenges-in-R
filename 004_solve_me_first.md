## CHALLENGE 004: Solve Me First

This is the first challenge on HackerRank to help get students acquanted with reading input and writing output (STDIN/STDOUT)

## Instructions (from HackerRank)

Complete the function solveMeFirst to compute the sum of two integers.

Function prototype:
    
    int solveMeFirst(int a, int b);

where,

a is the first integer input.
b is the second integer input
Return values

sum of the above two integers
Sample Input

a = 2
b = 3
Sample Output

5

Explanation

The sum of the two integers  and  is computed as: .


    ## MY SOLUTION

    input_raw <- readLines(con = "stdin")

    inp_a <- as.numeric(input_raw)[1]
    inp_b <- as.numeric(input_raw)[2]

    sum_of_intgrs <- inp_a + inp_b

    write.table(sum_of_intgrs, append = T, row.names = F, col.names = F)
