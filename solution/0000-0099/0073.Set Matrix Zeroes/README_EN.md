# [73. Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes)

[中文文档](/solution/0000-0099/0073.Set%20Matrix%20Zeroes/README.md)

## Description

<p>Given a <em>m</em> x <em>n</em> matrix, if an element is 0, set its entire row and column to 0. Do it <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank"><strong>in-place</strong></a>.</p>

<p><strong>Example 1:</strong></p>

<pre>

<strong>Input:</strong> 

[

&nbsp; [1,1,1],

&nbsp; [1,0,1],

&nbsp; [1,1,1]

]

<strong>Output:</strong> 

[

&nbsp; [1,0,1],

&nbsp; [0,0,0],

&nbsp; [1,0,1]

]

</pre>

<p><strong>Example 2:</strong></p>

<pre>

<strong>Input:</strong> 

[

&nbsp; [0,1,2,0],

&nbsp; [3,4,5,2],

&nbsp; [1,3,1,5]

]

<strong>Output:</strong> 

[

&nbsp; [0,0,0,0],

&nbsp; [0,4,5,0],

&nbsp; [0,3,1,0]

]

</pre>

<p><strong>Follow up:</strong></p>

<ul>
    <li>A straight forward solution using O(<em>m</em><em>n</em>) space is probably a bad idea.</li>
    <li>A simple improvement uses O(<em>m</em> + <em>n</em>) space, but still not the best solution.</li>
    <li>Could you devise a constant space solution?</li>
</ul>

## Solutions

<!-- tabs:start -->

### **Python3**

Solution 1:

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m, n = len(matrix), len(matrix[0])
        zero_rows = [False] * m
        zero_cols = [False] * n
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0:
                    zero_rows[i] = zero_cols[j] = True
        for i in range(m):
            for j in range(n):
                if zero_rows[i] or zero_cols[j]:
                    matrix[i][j] = 0
```

Solution 2:

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m, n = len(matrix), len(matrix[0])
        first_row_has_zero = any(matrix[0][j] == 0 for j in range(n))
        first_col_has_zero = any(matrix[i][0] == 0 for i in range(m))

        for i in range(1, m):
            for j in range(1, n):
                if matrix[i][j] == 0:
                    matrix[i][0] = matrix[0][j] = 0

        for i in range(1, m):
            for j in range(1, n):
                if matrix[i][0] == 0 or matrix[0][j] == 0:
                    matrix[i][j] = 0

        if first_row_has_zero:
            for j in range(n):
                matrix[0][j] = 0

        if first_col_has_zero:
            for i in range(m):
                matrix[i][0] = 0
```

### **Java**

Solution 1:

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        boolean[] zeroRows = new boolean[m];
        boolean[] zeroCols = new boolean[n];
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (matrix[i][j] == 0) {
                    zeroRows[i] = zeroCols[j] = true;
                }
            }
        }
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (zeroRows[i] || zeroCols[j]) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```

Solution 2:

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        boolean firstRowHasZero = false;
        boolean firstColHasZero = false;
        for (int j = 0; j < n; ++j) {
            if (matrix[0][j] == 0) {
                firstRowHasZero = true;
                break;
            }
        }
        for (int i = 0; i < m; ++i) {
            if (matrix[i][0] == 0) {
                firstColHasZero = true;
                break;
            }
        }
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = matrix[0][j] = 0;
                }
            }
        }
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }
        if (firstRowHasZero) {
            for (int j = 0; j < n; ++j) {
                matrix[0][j] = 0;
            }
        }
        if (firstColHasZero) {
            for (int i = 0; i < m; ++i) {
                matrix[i][0] = 0;
            }
        }
    }
}
```

### **C++**

```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int m = matrix.size(), n = matrix[0].size();
        vector<bool> zeroRows(m), zeroCols(n);
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 0) {
                    zeroRows[i] = zeroCols[j] = true;
                }
            }
        }
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (zeroRows[i] || zeroCols[j]) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
};
```

### **...**

```

```

<!-- tabs:end -->
