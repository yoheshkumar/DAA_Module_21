# EX 3D Pattern Matching
## DATE:
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.

## Algorithm:

1. **Initialize Pointers:**  
   - Set `i` to `0` to traverse the main string `s1`.  
   - Set `j` to `0` to traverse the pattern string `s2`.  

2. **Traverse Both Strings:**  
   - While `i` is less than the length of `s1` and `j` is less than the length of `s2`:  
     - If the characters at `s1[i]` and `s2[j]` match, increment both `i` and `j`.  
     - Otherwise, reset `i` to `i - j + 1` and `j` to `0` to restart the matching from the next position in `s1`.  

3. **Check for Match Completion:**  
   - If `j` equals the length of `s2`, a complete match is found. Return the starting index of the match in `s1` as `i - len(s2)`.  

4. **Return Result:**  
   - If no match is found, return `0` (or alternatively, could return `-1` to indicate no match).  

## Program:
```
/*
Program to implement the Pattern Matching.

Developed by: YOHESH KUMAR R.M
Register Number: 212222240118
*/

def BF(s1,s2):
    i = 0
    j = 0
    while(i < len(s1) and j < len(s2)):
        if(s1[i] ==  s2[j]):
            i += 1
            j += 1
        else:
            i = i - j + 1
            j = 0
    if(j >= len(s2)):
        return i - len(s2)
    else:
        return 0
if __name__ == "__main__":
    a1=input() 
    a2=input() 
    b=BF(a1,a2)
    print(b)

```

## Output:

![image](https://github.com/user-attachments/assets/0f294cc2-f4ee-47df-bc43-cb804a6101a9)

## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
