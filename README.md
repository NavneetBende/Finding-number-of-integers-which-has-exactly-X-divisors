# Finding-number-of-integers-which-has-exactly-X-divisors

Find Number of integers which has exactly x divisors using java
Our Aim is to find the Number of integers which has exactly X divisors using Java programming language.

In This program the user gives  a range and the number of divisors(say N), and divisors of every number in between the range are counted and compared with N.

Number of integers which has exactly x divisors using java
Method Discussed :
Method 1 : Naive approach
Method 2 : Efficient approach
Method 1 :
Declare a variable count =0, to count the required numbers with x factors.
Run a loop for range 1 to n.
Inside that take a variable count_factors = 0, that will count the factors of ith.
Now, run a inner loop.
And increase the count_factors if it’s is factor of ith number.
Check if count_factors == X, then increment the count by 1.
At last print the count value.
Method 1 : Code in Java
Run
//Write a program to count Number of integers which has exactly X divisors using Java
import java.util.*;
 
class Main{
    public static void main(String[] args)
    {
        int  n = 7, x = 2 ;
        int count = 0;
    
        for(int i=1; i<=n; i++){
        
            //variable to count the factors of i-th number
            int count_factors = 0;
            for(int j = 1; j<= i; j++){
                if(i%j==0){
                    count_factors++;
                }
            }
        
        if(count_factors == x)
            count++;
    }
        System.out.println(count);
    }
}
Output :
4
Related Pages
Counting number of days in a given month of a year
 
Finding Number of times x digit occurs in a given input
 
Finding Roots of a quadratic equation

Power of a Number 

Prime Number

Method 2 :
In this method we will use the efficient way for counting the factors that used in method 1.

Method 2 : Code in Java
Run
//Write a program to count Number of integers which has exactly X divisors using Java
import java.util.*;
 
class Main{

static void sieve(boolean[] primes, int x)
{
    primes[1] = true;
 
    for (int i=2; i*i <= x; i++)
    {
        if (primes[i] == false)
        {
            for (int j=2; j*i <= x; j++)
                primes[i*j] = true;
        }
    }
}

static int nDivisors(boolean[] primes, int x, int a, int b, int n)
{
    int result = 0;
 
    ArrayList<Integer> v=new ArrayList<>();
    for (int i = 2; i <= x; i++)
        if (primes[i] == false)
            v.add(i);
     
    
    for (int i=a; i<=b; i++)
    {
        int temp = i;
 
        int total = 1;
        int j = 0;
 
        for (int k = v.get(j); k*k <= temp; k = v.get(++j))
        {

            int count = 0;
 
            while (temp%k == 0){
                count++;
                temp = temp/k;
            }
 
            total = total*(count+1);
             
        }
 
        if (temp != 1)
            total = total*2;
 
        if (total == n)
            result++;
    }
    return result;
}
 
static int countNDivisors(int a, int b, int n)
{
    int x = (int)Math.sqrt(b) + 1;
 
    boolean[] primes=new boolean[x+1];
 
    sieve(primes, x);
 
    return nDivisors(primes, x, a, b, n);
}
 
// driver code
public static void main(String[] args)
{
    int  n = 7, x = 2 ;
    System.out.println(countNDivisors(1, n, x));
  
}
}
Output :
4
