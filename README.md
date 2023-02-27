# mersenne-prime-numbers

Here's an example of a bash script that outputs the Mersenne prime numbers:
~~~
#!/bin/bash

echo "Enter the number of Mersenne primes to output:"
read n

# Initialize variables for the first Mersenne prime and the next power of 2
mersenne=3
power=2

# Loop through n Mersenne primes and output each one
for (( i=0; i<n; i++ ))
do
    echo "$mersenne"
    power=$((power+1))
    mersenne=$(( (2**power) - 1 ))
    
    # Check if the new number is prime
    is_prime=1
    for (( j=2; j<=(mersenne/2); j++ ))
    do
        if (( mersenne % j == 0 )); then
            is_prime=0
            break
        fi
    done
    
    # If the new number is not prime, try the next power of 2
    while (( is_prime == 0 ))
    do
        power=$((power+1))
        mersenne=$(( (2**power) - 1 ))
        
        is_prime=1
        for (( j=2; j<=(mersenne/2); j++ ))
        do
            if (( mersenne % j == 0 )); then
                is_prime=0
                break
            fi
        done
    done
done
~~~

This script prompts the user to enter the number of Mersenne primes to output. It then uses a for loop to iterate through the specified number of primes and output each one. The loop calculates each Mersenne prime by raising 2 to the power of the next integer and subtracting 1. It then checks if the new number is prime by testing whether it is divisible by any integer from 2 to half of the number. If the number is not prime, the script increments the power of 2 and tries again until it finds a Mersenne prime.

To run this script, save it to a file with a .sh extension (e.g. mersenne.sh), make the file executable with the command chmod +x mersenne.sh, and then run it with the command ./mersenne.sh.
