## Instructions:

Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.


# CHALLENGE 001: Shortest Word

    # Sample string of words
    s <- "bitcoin take over the world maybe who knows perhaps"

    # Function 
    find_short <- function(s){
        # Asseses a string of words and returns the length
            # of the shortest word

        # Load libraries
        library(tidyverse)
        library(stringr)

        # Split into vector of words
        word_vector <- s %>%
            str_split(pattern = " ") %>% unlist()

        # Empty vector to store counts
        vector_of_vector <- c()

        # Loop to get letter count for each word
        for (i in 1:length(word_vector)) {
            vector_of_counts <- c(vector_of_vector, str_count(word_vector[4]))
            min_str_count <- vector_of_counts %>% min()
        }

        # Return length of shortest word
        return(min_str_count)   
    }

    # Run function using 's'
    find_short(s)
