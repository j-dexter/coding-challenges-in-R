## CHALLENGE 005: Jumping on Clouds (HackerRank) 

This challenge is from the Interview Preparation, KitWarm-up Challenges

## INSTRUCTIONS (from HackerRank)
Emma is playing a new mobile game that starts with consecutively numbered clouds. Some of the clouds are thunderheads and others are cumulus. She can jump on any cumulus cloud having a number that is equal to the number of the current cloud plus  or . She must avoid the thunderheads. Determine the minimum number of jumps it will take Emma to jump from her starting postion to the last cloud. It is always possible to win the game.

For each game, Emma will get an array of clouds numbered  if they are safe or if they must be avoided. For example,  indexed from . The number on each cloud is its index in the list so she must avoid the clouds at indexes  and . She could follow the following two paths:  or . The first path takes  jumps while the second takes .

### Function Description

Complete the jumpingOnClouds function in the editor below. It should return the minimum number of jumps required, as an integer.

jumpingOnClouds has the following parameter(s):

c: an array of binary integers

### Input Format

The first line contains an integer , the total number of clouds. The second line contains  space-separated binary integers describing clouds  where .

Constraints

### Output Format

Print the minimum number of jumps needed to win the game.

Sample Input 0

    7
    0 0 1 0 0 1 0

Sample Output 0

    4

Explanation 0: 
Emma must avoid  and . She can win the game with a minimum of jumps: 4


## MY SOLUTION

    # Enter your code here. Read input from STDIN. Print output to STDOUT

    # Get input
    input <- readLines(con='stdin')

    # Get n
    n <- as.numeric(input)[1]

    # Process cloud data
    clouds_raw  <- input[2]                         # Get raw cloud data
    clouds_splt <- strsplit(clouds_raw, " ")        # Split clouds to strings
    clouds_num  <- as.numeric(unlist(clouds_splt))  # String to integer conversion

    # Setup counters
    index = 1  # Tracks movement across cloud index
    jumps = 0  # Tracks number of jumps

    # While Loop for controlling when task is complete
    while (index < n) {

        # If statement to decide minimum jumps needed
        if ( (clouds_num[index + 2] == 0) & index < n-1) {
            jumps = jumps + 1
            index = index + 2
            #print("you jumped two spaces.")
        } else {
            jumps = jumps + 1
            index = index + 1
            #print("you cant jump two, bud did jump one.")
        }
    }

    # Output answer
    write.table(jumps, row.names = F, col.names = F)



