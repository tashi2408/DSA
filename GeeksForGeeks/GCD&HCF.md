## GCD or HCF of two numbers

##### Easy | C++ Code Solution Explanation

#### Problem

GCD (Greatest Common Divisor) or HCF (Highest Common Factor) of two numbers is the largest number that divides both of them.
For example, GCD of 20 and 28 is 4 and GCD of 98 and 56 is 14.

#### Naive Solution

- We take the min(a,b) and for ever number 'n' smaller than min(a, b) we check if `a%n==0` and `b%n==0`

#### Code

```
int gcd(int a, int b)
{
    int x = min(a, b);
    while(x>0){
        if(a%x==0 && b%x==0){
            break;
        }
        x--;
    }
    return x;
}
```

#### Complexity

Time Complexity: O(min(a, b))

Reason: The loop will run untill the min becomes zero(worst case) or we find common divisor.

Space Complexity: O(1)

Reason: No extra data structure is used.

#### Solution | Euclidean

- If a>b

- GCD(a, b) = GCD(a-b, b )

#### Code

```
int gcd(int a, int b)
{
    if(a==0 || b==0 )return 0;
    if(a==b)return a;

    if(a>b) return gcd(a-b, b);
    return gcd(a, b-a);
}
```

#### Complexity

Time Complexity: O(min(a, b))

Reason: The loop will run untill the min becomes zero(worst case) or we find common divisor.

Space Complexity: O(min(a, b))

Reason: Recursion stack takes space.

#### Solution | Extended Euclidean

- We continuously divide the bigger number by the smaller number.

- GCD(a, b) = GCD(b, a%b );

- We continously divide untill we get a 0(completly divisible).

#### Code

```
int gcd(int a, int b)
{
    if(b==0)return a;
    return gcd(b, a%b);
}
```

#### Complexity

Time Complexity: O(log(min(a, b)))

Reason: The loop will run untill the number completly divide the other.

Space Complexity: O(log(min(a, b)))

Reason: Recursion stack takes space.
