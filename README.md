# Abundant-Number-or-Not-in-C-Program

Abundant Number in C
In this program, we need to check if a number is an Abundant number in C Programming. A number n is said to be Abundant Number to follow these condition

The sum of its proper divisors is greater than the number itself
The difference between these two values is called the abundance.
Ex:- Abundant number  12 having a proper divisor is 1, 2, 3, 4, 6 

The sum of these factors is 16 it is greater than 12 
So it is an Abundant number

Some other abundant numbers: 

18, 20, 30, 70, 78, 80, 84, 90, 96, 100, 104, 108, 120
abundant or not in c
Working:-
For user input num

Find all proper divisors of num
Calculate the sum of these divisors
If sum > num : Abundant number
Else, not an Abundant number

Method 1 
For user input num
Initialize sum = 0
Run a loop in the iteration of (i)
For each, i check if it is a divisor of num (num % i == 0)
If yes then add to the sum
Compare sum and num, if sum > num then its abundant number
Method 1 Code
Run
#include <stdio.h>

int main ()
{
    int num = 18, sum = 0;
    
    for(int i = 1; i < num; i++)
    {
        if(num % i == 0) 
            sum = sum + i; 
    }
if(sum > num){
 printf("%d is an Abundant Number\n",num);
 printf("Num: %d\nSum: %d\nAbundance: %d", num, sum, (sum-num)); 
} else
 printf("%d is not a Abundant Number",num); 
} 
// Time complexity: O(N) 
// Space complexity: O(1)
Output:-
18 is an Abundant Number
Num: 18
Sum: 21
Abundance: 3
While loop in C
Related Pages
Strong number

Perfect number

Harshad number

Automorphic number

Friendly pair

Method 2
This method uses observations that all factors come in pairs.

All Factors come in pairs
For n = a * b (For each a there exists a unique b)

Example : 100 (1,100), (2, 50), (4, 25), (5, 20), (10, 100)
Shorten the loop
We can shorten the loop running between [1, num] to [1, √num]

Since we will find all pairs before √num (n = sqrt(n) * sqrt(n))
Method 2 Code
Run
#include <stdio.h> 
#include <math.h>
int getSum(int num){
    
    int sum = 0;
    
    for(int i = 1; i < sqrt(num); i++)
    {
        if (num % i == 0)
        {
            // For num : (1, num) will always be pair of divisor
            // acc to def., we must ignore adding num itself as divisor
            // when calculating for abundant number
            if(i == 1)
                sum = sum + i;
            
            // Example For 100 (10,10) will be one of the pair
            // But, we should add value 10 to the sum just once
            else if(i == num/i)
                sum = sum + i;
            
            // add both pairs as divisors
            // For any divisor i, num/i will also be a divisor
            else
                sum = sum + i + num/i;
        }
    }
    return sum;
}

//main Program
int main()
{
    int num=10;
    
  
    
    int sum = getSum(num);
    if(sum > num)
    {
        printf("%d is an Abundant Number\n",num);
        printf("Num: %d\nSum: %d\nAbundance: %d", num, sum, (sum-num));
    }
    else
        printf("%d is not a Abundant Number",num);
}
// Time Complexity: O(√N)
// Space Complexity: O(1)
Output:-
Enter a positive number: 100
100 is an Abundant Number
Num: 100
Sum: 107
Abundance: 7
Prime Course Trailer

Related Banners
Get PrepInsta Prime & get Access to all 200+ courses offered by PrepInsta in One Subscription

Get Prime
