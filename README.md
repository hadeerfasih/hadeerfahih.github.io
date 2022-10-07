# hadeerfahih.github.io
# 1- fibonacci Series using Recursion

#include<stdio.h>
int fib(int n)
{
    if (n <= 1)
        return n;
    return fib(n - 1) + fib(n - 2);
}

int main()
{
    int n = 9;
    printf("%d", fib(n));
    getchar();
    return 0;
}
**time complexity:** 0(2^n)
**space :**0(2)

## 2- fibonacci Series using Dynamic Programming
#include<stdio.h>

int fib(int n)
{
    /* Declare an array to store Fibonacci numbers. */
    int f[n + 1];
    int i;

    /* 0th and 1st number of the series are 0 and 1*/
    f[0] = 0;
    f[1] = 1;

    for (i = 2; i <= n; i++)
    {
        /* Add the previous 2 numbers in the series
            and store it */
        f[i] = f[i - 1] + f[i - 2];
    }

    return f[n];
}

int main()
{
    int n = 9;
    printf("%d", fib(n));
    getchar();
    return 0;
}
*time:*0(n)
*space:*0(n)

### 3- fibonacci Series using Space Optimized Method
#include<stdio.h>
int fib(int n)
{
    int a = 0, b = 1, c, i;
    if (n == 0)
        return a;
    for (i = 2; i <= n; i++)
    {
        c = a + b;
        a = b;
        b = c;
    }
    return b;
}

int main()
{
    int n = 9;
    printf("%d", fib(n));
    getchar();
    return 0;
}
//time:0(n)
//space:0(1)

### 4- Divide and conquer 

#include <stdio.h>
 
void multiply(int F[2][2], int M[2][2]);

void power(int F[2][2], int n);

/* function that returns nth Fibonacci number */
int fib(int n)
{
    int F[2][2] = { {1,1},{1,0} };
    if (n == 0)
        return 0;
    power(F, n - 1);
    return F[0][0];
}

/* Optimized version of power() in method 4 */
void power(int F[2][2], int n)
{
    if (n == 0 || n == 1)
        return;
    int M[2][2] = { {1,1},{1,0} };

    power(F, n / 2);
    multiply(F, F);

    if (n % 2 != 0)
        multiply(F, M);
}

void multiply(int F[2][2], int M[2][2])
{
    int x = F[0][0] * M[0][0] + F[0][1] * M[1][0];
    int y = F[0][0] * M[0][1] + F[0][1] * M[1][1];
    int z = F[1][0] * M[0][0] + F[1][1] * M[1][0];
    int w = F[1][0] * M[0][1] + F[1][1] * M[1][1];

    F[0][0] = x;
    F[0][1] = y;
    F[1][0] = z;
    F[1][1] = w;
}

/* Driver program to test above function */
int main()
{
    int n = 9;
    printf("%d", fib(9));
    getchar();
    return 0;
}
