# [657. Robot Return to Origin](https://leetcode.com/problems/robot-return-to-origin)

[中文文档](/solution/0600-0699/0657.Robot%20Return%20to%20Origin/README.md)

## Description

<p>There is a robot starting at position (0, 0), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot <strong>ends up at (0, 0)</strong> after it completes its moves.</p>

<p>The move sequence is represented by a string, and the character moves[i] represents its ith move. Valid moves are R (right), L (left), U (up), and D (down). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.</p>

<p><strong>Note</strong>: The way that the robot is &quot;facing&quot; is irrelevant. &quot;R&quot; will always make the robot move to the right once, &quot;L&quot; will always make it move left, etc. Also, assume that the magnitude of the robot&#39;s movement is the same for each move.</p>

<p><b>Example 1:</b></p>

<pre>

<b>Input:</b> &quot;UD&quot;

<b>Output:</b> true 

<strong>Explanation</strong>: The robot moves up once, and then down once. All moves have the same magnitude, so it ended up at the origin where it started. Therefore, we return true.

</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>

<b>Input:</b> &quot;LL&quot;

<b>Output:</b> false

<strong>Explanation</strong>: The robot moves left twice. It ends up two &quot;moves&quot; to the left of the origin. We return false because it is not at the origin at the end of its moves.

</pre>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def judgeCircle(self, moves: str) -> bool:
        x = y = 0
        for c in moves:
            if c == 'R':
                x += 1
            elif c == 'L':
                x -= 1
            elif c == 'U':
                y += 1
            elif c == 'D':
                y -= 1
        return x == 0 and y == 0
```

### **Java**

```java
class Solution {
    public boolean judgeCircle(String moves) {
        int x = 0, y = 0;
        for (int i = 0; i < moves.length(); ++i) {
            char c = moves.charAt(i);
            if (c == 'R') ++x;
            else if (c == 'L') --x;
            else if (c == 'U') ++y;
            else if (c == 'D') --y;
        }
        return x == 0 && y == 0;
    }
}
```

### **...**

```

```

<!-- tabs:end -->
