### mixing.txt
```
2 5 3
3 3
8 10
15 15
20 13
8 7
12 10
5 5
18 6
6 10
4 8

```

### Python Solution
```py
def kapsack(Volumes, Values, capacity):
  n = len(Volumes)
  dp = [[0]*(capacity+1) for _ in range(n+1)]
  for i in range(1, n+1):
    for j in range(1, capacity+1):
      if Volumes[i-1] > j:
        dp[i][j] = dp[i-1][j]
      else:
        dp[i][j] = max(Values[i-1] + dp[i-1][j - Volumes[i-1]], dp[i-1][j])
  return dp[n][capacity]

with open('mixing.txt', 'r') as f:
  length, width, height = map(int, f.readline().strip().split()) # 1st line
  capacity = length * width * height
  X, Y = map(int, f.readline().strip().split()) # 2nd line
  for _ in range(X):
    Volumes, Values = [], []
    for _ in range(Y):
      volume, value = map(int, f.readline().strip().split())
      Volumes.append(volume); Values.append(value)
    print(kapsack(Volumes, Values, capacity))

```

### Java Solution
```java
import java.util.*;
import java.io.*;

class Main {
  public static void main(String[] args) throws FileNotFoundException {
    Scanner sc = new Scanner(new File("mixing.txt"));
    // 1st line
    String[] tmp = sc.nextLine().split(" ");
    int capacity = 1;
    for (String unit : tmp) {
      capacity *= Integer.valueOf(unit);
    }
    // 2nd line
    tmp = sc.nextLine().split(" ");
    int X = Integer.valueOf(tmp[0]), Y = Integer.valueOf(tmp[1]);
    // loop through X sets
    while(X-- > 0) {
      int[] volumes = new int[Y], values = new int[Y];
      for (int i=0; i<Y; i++) {
        tmp = sc.nextLine().split(" ");
        int volume = Integer.valueOf(tmp[0]), value = Integer.valueOf(tmp[1]);
        volumes[i] = volume; values[i] = value;
      }
      int ans = knapsack(volumes, values, capacity);
      System.out.println(ans);
    }
  }

  private static int knapsack(int[] volumes, int[] values, int capacity) {
    int[][] dp = new int[values.length+1][capacity+1];
    for (int i = 1; i <= values.length; i++) {
      for (int j = 1; j <= capacity; j++) {
        if (volumes[i-1] > j) {
          dp[i][j] = dp[i-1][j];
        } else {
          dp[i][j] = Math.max(values[i-1] + dp[i-1][j - volumes[i-1]], dp[i-1][j]);
        }
      }
    }
    return dp[values.length][capacity];
  }
}
```
