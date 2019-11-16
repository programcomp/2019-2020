### Python Solution
```py
with open('fizzBuzzBloop.txt', 'r') as f:
 start = int(f.readline().strip())
 end = int(f.readline().strip())
 n = int(f.readline().strip())
 res = ['']*(end+1) # Create a result table
 for _ in range(n):
   tmp = f.readline().strip().split()
   num, text = int(tmp[0]), tmp[1]
   # append multiples of num to the result table
   for i in range(num, end+1, num):
     res[i] += text
 for i, s in enumerate(res):  # fill numbers
   if s == '':
     res[i] = str(i)
 # only return result from start position
 print('\n'.join(res[start:]))
```
