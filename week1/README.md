# Sample answers for Homework Week1

## Create Triangle

### Python
```py
def buildTriangle(n):
  for i in range(n):
    if i == n - 1: # bottom
      print('/' + '_'*2*i + '\\')
    else:
      print(' '*(n-i-1) + '/' + ' '*2*i + '\\' + ' '*(n-i-1))

T = int(input())
ar = []
for _ in range(T):
  n = int(input())
  ar.append(n)
  
for n in ar:
  buildTriangle(n)

```


### Java (11)
```java
import java.util.*;
public class Main {
    private static void solve(int n) {
        for (int i=0; i<n; i++) {
            StringBuilder sb = new StringBuilder();
            if (i == n-1) { // Bottom
                sb.append("/")
                        .append("_".repeat(2*i))
                        .append("\\");
            } else {
                sb.append(" ".repeat(n-i-1))
                        .append("/")
                        .append(" ".repeat(2*i))
                        .append("\\")
                        .append(" ".repeat((n-i-1)));
            }
            System.out.println(sb.toString());
        }
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        for (int i=0; i<T; i++) {
            int n = sc.nextInt();
            solve(n);
        }
        sc.close();
    }
}
```
