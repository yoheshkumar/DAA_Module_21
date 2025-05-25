# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm:

1. **Initialize the DP Table:**  
   - Create a 2D `dp` array where `dp[i][mask]` represents whether there exists a Hamiltonian path ending at node `i` with the set of visited nodes represented by `mask`.  
   - Set `dp[i][1 << i]` to `True` for each node `i`, as each node can start a path by itself.  

2. **Fill the DP Table:**  
   - Iterate through all possible node sets (represented by `mask`) and each node `j`.  
   - If node `j` is part of the current `mask`, try to extend the path:  
     - For each potential previous node `k` in the `mask`, check if:  
       - `k` is connected to `j` in the adjacency matrix.  
       - Removing `j` from the current `mask` still forms a valid Hamiltonian path ending at `k`.  
     - If these conditions are met, set `dp[j][mask]` to `True`.  

3. **Check for a Hamiltonian Path:**  
   - After filling the DP table, check if any node can reach a state where all nodes are visited (`(1 << N) - 1`).  
   - If found, return **True**.  

4. **Return the Result:**  
   - If no Hamiltonian path is found, return **False**. 

## Program:
```
/*
Program to implement to check whether Hamiltonian path exits in the given graph.

Developed by: YOHESH KUMAR R.M 
Register Number: 212222240118
*/

def Hamiltonian_path(adj, N):
    #Start here
    dp = [[False for i in range(1 << N)] for j in range(N)]
    for i in range(N):
        dp[i][1 << i] = True
    for i in range(1 << N):
        for j in range(N):
            if ((i & (1 << j)) != 0):
 
                for k in range(N):
                    if ((i & (1 << k)) != 0 and
                             adj[k][j] == 1 and
                                     j != k and
                          dp[k][i ^ (1 << j)]):
                        dp[j][i] = True
                        break
    for i in range(N):
        if (dp[i][(1 << N) - 1]):
            return True
    return False
adj = [ [ 0, 1, 1, 1, 0 ] ,
        [ 1, 0, 1, 0, 1 ],
        [ 1, 1, 0, 1, 1 ],
        [ 1, 0, 1, 0, 0 ] ]
 
N = len(adj)
if (Hamiltonian_path(adj, N)):
    print("YES")
else:
    print("NO")
```

## Output:

![image](https://github.com/user-attachments/assets/c11c5d1b-712d-44f9-a594-5124d4c532da)


## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
