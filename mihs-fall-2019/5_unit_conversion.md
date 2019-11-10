### unitConversion.txt
```
4
c 126
c 225335
i 50
i 93
```

### Python Solution
```py
with open('unitConversion.txt', 'r') as f:
  tc = int(f.readline().strip())
  for _ in range(tc):
    A = f.readline().strip().split()
    x = float(A[1])
    kilometer = meter = 0.0
    if A[0] == 'i': # inch
      x = x * 2.54 # convert to centimeter
    kilometer = x // 100000
    x = x % 100000
    meter = x // 100
    x = x % 100
    print(round(kilometer), round(meter), round(x))
```

### Java Solution
```java
import java.util.*; // For Scanner
import java.io.*; // For File

class Main {
 public static void main(String[] args) throws FileNotFoundException {
   Scanner sc = new Scanner(new File("unitConversion.txt"));
   int tc = Integer.valueOf(sc.nextLine()); // read 1st line
   while (tc-- > 0) {
     String[] A = sc.nextLine().split(" "); 
     double x = Double.valueOf(A[1]);
     if (A[0].equals("i")) {
      x *= 2.54; // convert to centimeter
     }
     double kilometer = x / 100000;
     x = x % 100000;
     double meter = x / 100;
     x = x % 100;
     System.out.printf("%d %d %d\n", Math.round(kilometer), Math.round(meter), Math.round(x));
   }
 }
}

```
