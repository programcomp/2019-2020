### missingPrices.txt
```
3
X 7 150
10 10 X
10 X 20
```

### Sample Solution - Python

```py
with open('missingPrices.txt', 'r') as f:
  tc = int(f.readline().strip())
  for _ in range(tc):
    A = f.readline().strip().split()
    x = 0.0
    if A[0] == 'X': # Case 1
      x = 100 * float(A[2]) / (100.0 + float(A[1]))
    elif A[1] == 'X': # Case 2
      x = 100 * (float(A[2]) - float(A[0])) / float(A[0])
    elif A[2] == 'X': # Case 3
      x = (100 * float(A[0]) + float(A[0])*float(A[1])) / 100
    else:
      raise ValueError('X is not found')
    print(round(x, 2)) 
```

### Sample Soluton - Java (Main.java)
```java
import java.util.*; // For Scanner
import java.io.*; // For File

class Main {
 public static void main(String[] args) throws FileNotFoundException {
   Scanner sc = new Scanner(new File("missingPrices.txt"));
   int tc = Integer.valueOf(sc.nextLine()); // read 1st line
   while (tc-- > 0) {
     String[] A = sc.nextLine().split(" "); double x = 0.0;
     if (A[0].equals("X")) { // Case 1
      x = 100 * Double.valueOf(A[2]) / (100.0 + Double.valueOf(A[1]));
     } else if (A[1].equals("X")) { // Case 2
      x = 100 * (Double.valueOf(A[2]) - Double.valueOf(A[0])) / Double.valueOf(A[0]);
     } else if (A[2].equals("X")) {
       x = (100 * Double.valueOf(A[0]) + Double.valueOf(A[0]) * Double.valueOf(A[1])) / 100.0;
     } else {
      throw new IllegalArgumentException("X is not found");
     }
     System.out.println(Math.round(x * 100.0) / 100.0); // Round to 2 decimal points
   }
 }
}

```
