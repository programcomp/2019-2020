### Magic Square

#### Input file (magic.txt)
```
2
5 6 4
7 8 9
3 1 2
4 1 7
3 9 6
8 5 2

```

#### Sample Solution (Python)
```py
def solve(A):
  res = 0
  
  for row in A: # check rows
    if sum(row) != 15:
      res += 1
  
  for col in zip(*A): # check cols
    if sum(col) != 15:
      res += 1
  # diagonal
  if sum(A[i][i] for i in range(3)) != 15:
    res += 1
  # anti-diagonal
  if sum(A[i][~i] for i in range(3)) != 15:
    res += 1

  return res

with open('magic.txt', 'r') as f:
  TC = int(f.readline().strip())
  for _ in range(TC):
    A = []
    for _ in range(3):
      a, b, c = map(int, f.readline().strip().split())
      A.append((a,b,c))
    print(solve(A))

```
