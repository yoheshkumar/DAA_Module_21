# EX 3A Knight Tour & Count Path
## DATE:
## AIM:
To write a python program to find minimum steps to reach to specific cell in minimum moves by knight

## Algorithm:

1. **Initialize Movement Arrays:**  
   - Define two arrays, `dx` and `dy`, representing the 8 possible moves a knight can make on a chessboard.  

2. **Setup the Queue for BFS:**  
   - Use a queue to perform a **Breadth-First Search (BFS)**.  
   - Enqueue the knight’s starting position with a distance of 0 and mark it as visited.  

3. **Process the BFS:**  
   - While the queue is not empty:  
     - Dequeue the front cell.  
     - If the current cell matches the target position, return its distance as the minimum steps required.  
     - Otherwise, explore all 8 possible knight moves.  
     - For each valid move (within bounds and not visited), mark it as visited and enqueue it with an incremented distance.  

4. **Return the Result:**  
   - If the target position is reached during BFS, return the distance.  
   - If the queue is exhausted without reaching the target, the target is unreachable (though this won’t happen for a properly defined chessboard).  

## Program:
```
/*
Program to implement to find minimum steps to reach to specific cell in minimum moves by knight.

Developed by: YOHESH KUMAR R.M
Register Number: 212222240118
*/

class cell:
    def __init__(self, x = 0, y = 0, dist = 0):
        self.x = x
        self.y = y
        self.dist = dist

def isInside(x, y, N):
    if (x >= 1 and x <= N and
        y >= 1 and y <= N):
        return True
    return False

def minStepToReachTarget(knightpos, targetpos, N):
    # add your code here
    dx = [2, 2, -2, -2, 1, 1, -1, -1]
    dy = [1, -1, 1, -1, 2, -2, 2, -2]
 
    queue = []
    queue.append(cell(knightpos[0], knightpos[1], 0))
 
    visited = [[False for i in range(N + 1)]
               for j in range(N + 1)]
 
    visited[knightpos[0]][knightpos[1]] = True
    while(len(queue) > 0):
        t = queue[0]
        queue.pop(0)
        if(t.x == targetpos[0] and
           t.y == targetpos[1]):
            return t.dist
 
        for i in range(8):
            x = t.x + dx[i]
            y = t.y + dy[i]
 
            if(isInside(x, y, N) and not visited[x][y]):
                visited[x][y] = True
                queue.append(cell(x, y, t.dist + 1))
    
if __name__=='__main__':
    N = 30
    knightpos = [1, 1]
    targetpos = [30, 30]
    print(minStepToReachTarget(knightpos, targetpos, N))
```

## Output:

![image](https://github.com/user-attachments/assets/76ffcdc6-8947-4b63-a2a9-f553b8bd18d0)


## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.
