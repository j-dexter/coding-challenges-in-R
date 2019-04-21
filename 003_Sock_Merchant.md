

# The Sock Merchant challenge from HackerRank

# My Solution

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
