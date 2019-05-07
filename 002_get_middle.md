## CHALLENGE 002: Get Middle Character(s)

## Instructions

You are going to be given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.


# My Solution

      library(tidyverse)
      library(stringr)

      # Sample string of words
      odd_str <- "testing"
      even_str <- "test"

      get_middle <- function(word_string){
         # Given a word as an input, give the center character(s) as output.

         # Get count of characters in word
         n <- nchar(word_string) 

         # Split string and save characters to vector
         character_vector <- str_split(word_string, pattern = "") %>% unlist()

         # Check if 'n' is even: if so, get center '2' characters 
         if((n %% 2) == 0) {
             cnt_chr <- str_c(character_vector[n/2], character_vector[n/2 + 1])

         # Else odd (no remainder): get just the center character
         } else {
             cnt_chr <- character_vector[n/2 + 0.5]
         }

         # Return center character(s)
         return(cnt_chr)
         }

     # Test Function
     get_middle(even_str)
     get_middle(odd_str)
