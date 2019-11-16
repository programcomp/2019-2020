### itoa.txt
```
4
2 8 5
16 10 464367618
2 16 24
15 12 1B
```

### Python Solution
```py
hex_string = '0123456789ABCDEF'
def toDec(base, num_str):
  map = {c:i for i, c in enumerate(hex_string)}
  res = 0
  for i, c in enumerate(num_str[::-1]):
    res =  map[c]*(base**i) + res
  return res

def convert(num, base):
  map = {i:c for i, c in enumerate(hex_string)}
  res = ''
  while num > 0:
    res = map[num % base] + res
    num //= base
  return res

with open('itoa.txt','r') as f:
  tc = int(f.readline().strip())
  for _ in range(tc):
    A = f.readline().strip().split()
    to_base, cur_base, num_str = int(A[0]), int(A[1]), A[2]
    num = toDec(cur_base, num_str) # Convert to decimal
    ans = convert(num, to_base) # Convert to base
    print(ans)
```
