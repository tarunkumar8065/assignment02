# Assignment 2 — Shell Programming

> A collection of 12 shell programs covering fundamental concepts: conditionals, loops, switch-case, string operations, file pattern search, and system commands.

---

## How to Run

```bash
# Make any script executable
chmod +x <script_name>.sh

# Run the script
./<script_name>.sh
```

---

## Program 1: Check Positive or Negative Number

**Aim:** To write a program to identify whether the given number is positive or negative using shell programming.

**Code:** [`q1_positive_negative.sh`](q1_positive_negative.sh)
```bash
#!/bin/bash
# Program 1: To identify whether a given number is positive or negative

echo "Enter a number: "
read num

if [ $num -gt 0 ]; then
    echo "$num is a Positive number."
elif [ $num -lt 0 ]; then
    echo "$num is a Negative number."
else
    echo "The number is Zero."
fi
```

**Sample Output:**
```
Enter a number:
25
25 is a Positive number.
```
```
Enter a number:
-7
-7 is a Negative number.
```
```
Enter a number:
0
The number is Zero.
```

---

## Program 2: Largest and Smallest of Three Numbers

**Aim:** To find the largest and smallest of three numbers using shell programming.

**Code:** [`q2_largest_smallest.sh`](q2_largest_smallest.sh)
```bash
#!/bin/bash
# Program 2: To find the largest and smallest of three numbers

echo "Enter three numbers: "
read a b c

# Find Largest
largest=$a
if [ $b -gt $largest ]; then
    largest=$b
fi
if [ $c -gt $largest ]; then
    largest=$c
fi

# Find Smallest
smallest=$a
if [ $b -lt $smallest ]; then
    smallest=$b
fi
if [ $c -lt $smallest ]; then
    smallest=$c
fi

echo "The three numbers are: $a, $b, $c"
echo "Largest number is: $largest"
echo "Smallest number is: $smallest"
```

**Sample Output:**
```
Enter three numbers:
45 12 78
The three numbers are: 45, 12, 78
Largest number is: 78
Smallest number is: 12
```

---

## Program 3: Sum and Average of N Numbers

**Aim:** To find the sum and average of N numbers using shell programming.

**Code:** [`q3_sum_average.sh`](q3_sum_average.sh)
```bash
#!/bin/bash
# Program 3: To find the sum and average of N numbers

echo "Enter the count of numbers (N): "
read n

sum=0
echo "Enter $n numbers: "
for (( i=1; i<=n; i++ ))
do
    read num
    sum=$((sum + num))
done

avg=$(echo "scale=2; $sum / $n" | bc)

echo "Sum = $sum"
echo "Average = $avg"
```

**Sample Output:**
```
Enter the count of numbers (N):
5
Enter 5 numbers:
10
20
30
40
50
Sum = 150
Average = 30.00
```

---

## Program 4: Factorial of a Number

**Aim:** To find the factorial of the given number using shell programming.

**Code:** [`q4_factorial.sh`](q4_factorial.sh)
```bash
#!/bin/bash
# Program 4: To find the factorial of a given number

echo "Enter a number: "
read num

fact=1
for (( i=1; i<=num; i++ ))
do
    fact=$((fact * i))
done

echo "Factorial of $num is: $fact"
```

**Sample Output:**
```
Enter a number:
6
Factorial of 6 is: 720
```

---

## Program 5: Sequence of Odd Numbers up to N

**Aim:** To write a program to find the sequence of odd numbers present up to given n number.

**Code:** [`q5_odd_numbers.sh`](q5_odd_numbers.sh)
```bash
#!/bin/bash
# Program 5: To find the sequence of odd numbers up to a given n

echo "Enter a number (n): "
read n

echo "Odd numbers from 1 to $n are:"
for (( i=1; i<=n; i+=2 ))
do
    echo -n "$i "
done
echo ""
```

**Sample Output:**
```
Enter a number (n):
15
Odd numbers from 1 to 15 are:
1 3 5 7 9 11 13 15
```

---

## Program 6: Sum of Series (1² + 2² + 3² + … + n²)

**Aim:** To write a program to find the sum of series S = 1² + 2² + 3² + … + n² using shell programming.

**Code:** [`q6_sum_of_squares.sh`](q6_sum_of_squares.sh)
```bash
#!/bin/bash
# Program 6: To find the sum of series S = 1^2 + 2^2 + 3^2 + ... + n^2

echo "Enter the value of n: "
read n

sum=0
for (( i=1; i<=n; i++ ))
do
    sum=$((sum + i*i))
done

echo "Sum of series 1^2 + 2^2 + 3^2 + ... + ${n}^2 = $sum"
```

**Sample Output:**
```
Enter the value of n:
5
Sum of series 1^2 + 2^2 + 3^2 + ... + 5^2 = 55
```

> **Verification:** 1² + 2² + 3² + 4² + 5² = 1 + 4 + 9 + 16 + 25 = 55 ✓

---

## Program 7: Arithmetic Operations Using Switch Case

**Aim:** To write a shell program to perform the arithmetic operation using switch case.

**Code:** [`q7_arithmetic_switch.sh`](q7_arithmetic_switch.sh)
```bash
#!/bin/bash
# Program 7: To perform arithmetic operations using switch case

echo "Enter two numbers: "
read a b

echo "Select an operation:"
echo "1. Addition"
echo "2. Subtraction"
echo "3. Multiplication"
echo "4. Division"
echo "Enter your choice (1-4): "
read choice

case $choice in
    1) result=$((a + b))
       echo "$a + $b = $result" ;;
    2) result=$((a - b))
       echo "$a - $b = $result" ;;
    3) result=$((a * b))
       echo "$a * $b = $result" ;;
    4) if [ $b -ne 0 ]; then
           result=$(echo "scale=2; $a / $b" | bc)
           echo "$a / $b = $result"
       else
           echo "Error: Division by zero!"
       fi ;;
    *) echo "Invalid choice!" ;;
esac
```

**Sample Output:**
```
Enter two numbers:
24 6
Select an operation:
1. Addition
2. Subtraction
3. Multiplication
4. Division
Enter your choice (1-4):
1
24 + 6 = 30
```
```
Enter two numbers:
24 6
Enter your choice (1-4):
4
24 / 6 = 4.00
```

---

## Program 8: Length of a String

**Aim:** To write a shell program to find the length of the string.

**Code:** [`q8_string_length.sh`](q8_string_length.sh)
```bash
#!/bin/bash
# Program 8: To find the length of a string

echo "Enter a string: "
read str

length=${#str}

echo "The string is: \"$str\""
echo "Length of the string is: $length"
```

**Sample Output:**
```
Enter a string:
Shell Programming
The string is: "Shell Programming"
Length of the string is: 17
```

---

## Program 9: Pattern Search Using File

**Aim:** To write a shell program to perform various pattern search using file.

**Code:** [`q9_pattern_search.sh`](q9_pattern_search.sh)
```bash
#!/bin/bash
# Program 9: To perform various pattern search using file

FILENAME="sample.txt"

# Create a sample file for demonstration
cat > $FILENAME << EOF
Hello World
Shell Programming is fun
Linux is an open source operating system
Bash shell scripting is powerful
Hello from the other side
Programming in shell is interesting
EOF

echo "Contents of $FILENAME:"
echo "========================"
cat $FILENAME
echo "========================"
echo ""

# 1. Search for a specific pattern
echo "1. Lines containing 'Shell':"
grep "Shell" $FILENAME
echo ""

# 2. Case-insensitive search
echo "2. Case-insensitive search for 'hello':"
grep -i "hello" $FILENAME
echo ""

# 3. Count occurrences of a pattern
echo "3. Count of lines containing 'is':"
grep -c "is" $FILENAME
echo ""

# 4. Display line numbers with matching pattern
echo "4. Lines containing 'programming' (with line numbers, case-insensitive):"
grep -in "programming" $FILENAME
echo ""

# 5. Invert match - lines NOT containing the pattern
echo "5. Lines NOT containing 'is':"
grep -v "is" $FILENAME
echo ""

# Clean up
rm -f $FILENAME
```

**Sample Output:**
```
Contents of sample.txt:
========================
Hello World
Shell Programming is fun
Linux is an open source operating system
Bash shell scripting is powerful
Hello from the other side
Programming in shell is interesting
========================

1. Lines containing 'Shell':
Shell Programming is fun

2. Case-insensitive search for 'hello':
Hello World
Hello from the other side

3. Count of lines containing 'is':
4

4. Lines containing 'programming' (with line numbers, case-insensitive):
2:Shell Programming is fun
6:Programming in shell is interesting

5. Lines NOT containing 'is':
Hello World
Hello from the other side
```

---

## Program 10: Sum of Series Using Switch Case

**Aim:** To write a shell program to perform sum of series using switch case.

**Code:** [`q10_sum_series_switch.sh`](q10_sum_series_switch.sh)
```bash
#!/bin/bash
# Program 10: To perform sum of series using switch case

echo "Select a series to compute:"
echo "1. Sum of first N natural numbers (1+2+3+...+N)"
echo "2. Sum of squares (1^2+2^2+3^2+...+N^2)"
echo "3. Sum of cubes (1^3+2^3+3^3+...+N^3)"
echo "Enter your choice (1-3): "
read choice

echo "Enter the value of N: "
read n

case $choice in
    1) sum=0
       for (( i=1; i<=n; i++ ))
       do
           sum=$((sum + i))
       done
       echo "Sum of first $n natural numbers = $sum" ;;

    2) sum=0
       for (( i=1; i<=n; i++ ))
       do
           sum=$((sum + i*i))
       done
       echo "Sum of squares of first $n natural numbers = $sum" ;;

    3) sum=0
       for (( i=1; i<=n; i++ ))
       do
           sum=$((sum + i*i*i))
       done
       echo "Sum of cubes of first $n natural numbers = $sum" ;;

    *) echo "Invalid choice!" ;;
esac
```

**Sample Output:**
```
Select a series to compute:
1. Sum of first N natural numbers (1+2+3+...+N)
2. Sum of squares (1^2+2^2+3^2+...+N^2)
3. Sum of cubes (1^3+2^3+3^3+...+N^3)
Enter your choice (1-3):
1
Enter the value of N:
10
Sum of first 10 natural numbers = 55
```
```
Enter your choice (1-3):
3
Enter the value of N:
4
Sum of cubes of first 4 natural numbers = 100
```

> **Verification:** 1³ + 2³ + 3³ + 4³ = 1 + 8 + 27 + 64 = 100 ✓

---

## Program 11: Check Palindrome Number

**Aim:** To write a shell program to check whether a given number is palindrome or not.

**Code:** [`q11_palindrome.sh`](q11_palindrome.sh)
```bash
#!/bin/bash
# Program 11: To check whether a given number is palindrome or not

echo "Enter a number: "
read num

original=$num
reverse=0

while [ $num -gt 0 ]
do
    remainder=$((num % 10))
    reverse=$((reverse * 10 + remainder))
    num=$((num / 10))
done

if [ $original -eq $reverse ]; then
    echo "$original is a Palindrome number."
else
    echo "$original is NOT a Palindrome number."
fi
```

**Sample Output:**
```
Enter a number:
12321
12321 is a Palindrome number.
```
```
Enter a number:
4567
4567 is NOT a Palindrome number.
```

---

## Program 12: Check Login Connection

**Aim:** To write a program to check whether a login is connected or not.

**Code:** [`q12_login_check.sh`](q12_login_check.sh)
```bash
#!/bin/bash
# Program 12: To check whether a login is connected or not

echo "Enter the username to check: "
read username

if who | grep -q "^$username "; then
    echo "User '$username' is currently logged in."
    echo ""
    echo "Login details:"
    who | grep "^$username "
else
    echo "User '$username' is NOT currently logged in."
fi

echo ""
echo "Currently logged in users:"
who
```

**Sample Output:**
```
Enter the username to check:
kushagra
User 'kushagra' is currently logged in.

Login details:
kushagra  pts/0   2026-02-26 14:00 (192.168.1.5)

Currently logged in users:
kushagra  pts/0   2026-02-26 14:00 (192.168.1.5)
root      pts/1   2026-02-26 13:45 (192.168.1.1)
```
```
Enter the username to check:
john
User 'john' is NOT currently logged in.

Currently logged in users:
kushagra  pts/0   2026-02-26 14:00 (192.168.1.5)
root      pts/1   2026-02-26 13:45 (192.168.1.1)
```

---

## File Structure

```
2nd_Assignment/
├── README.md
├── q1_positive_negative.sh
├── q2_largest_smallest.sh
├── q3_sum_average.sh
├── q4_factorial.sh
├── q5_odd_numbers.sh
├── q6_sum_of_squares.sh
├── q7_arithmetic_switch.sh
├── q8_string_length.sh
├── q9_pattern_search.sh
├── q10_sum_series_switch.sh
├── q11_palindrome.sh
└── q12_login_check.sh
```
