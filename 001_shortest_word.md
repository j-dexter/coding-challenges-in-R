## Instructions:

Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.

find_short <- function(s){

    library(stringr)

    list_of_words <- s %>%
        str_split(pattern = " ") 

    list_of_counts <- c()
    
    for (i in 1:length(list_of_words[[1]])) {
        #word_i <- list_of_words[[1]][i]
        #print(list_of_words[[1]][i])
        list_of_counts <- c(list_of_counts, str_count(list_of_words[[1]][i]))
        min_str_count <- list_of_counts %>% min()
    }
    
    return(min_str_count)   
}
