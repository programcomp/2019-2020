### Python Solution
```py
with open('codedMessage.txt', 'r') as f:
 map = {}
 # build character map
 for i in range(26):
   x = f.readline().strip()
   map[x] = chr(i + ord('a'))
 map[f.readline().strip()] = '.'
 map[f.readline().strip()] = ' '

 A = f.readline().strip().split()
 print(''.join(map[c] for c in A))
 # The above is a one-liner for the following code
 # res = ''
 # for c in A:
 #   res += map[c]
 # print(res)
```
