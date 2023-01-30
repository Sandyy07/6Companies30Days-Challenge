(Leetcode Problem) 

Given the radius and the position of the center of a circle, implement the function randPoint which generates a uniform random point inside the circle.

Implement the Solution class:

Solution(double radius, double x_center, double y_center) initializes the object with the radius of the circle radius and the position of the center (x_center, y_center).
randPoint() returns a random point inside the circle. A point on the circumference of the circle is considered to be in the circle. The answer is returned as an array [x, y].
 

Example 1:

Input
["Solution", "randPoint", "randPoint", "randPoint"]
[[1.0, 0.0, 0.0], [], [], []]
Output
[null, [-0.02493, -0.38077], [0.82314, 0.38945], [0.36572, 0.17248]]

Explanation
Solution solution = new Solution(1.0, 0.0, 0.0);
solution.randPoint(); // return [-0.02493, -0.38077]
solution.randPoint(); // return [0.82314, 0.38945]
solution.randPoint(); // return [0.36572, 0.17248]


CODE (JAVA) :

```
class Solution {

    private double x, y, r;
    
    public Solution(double radius, double x_center, double y_center) {
        this.r = radius;
        this.x = x_center;
        this.y = y_center;
    }

    public double[] randPoint() {
        double deg = Math.random() * 2 * Math.PI;
        double len = Math.sqrt(Math.random()) * r;
        return new double[] {Math.cos(deg) * len + x, Math.sin(deg) * len + y};
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-30 114456](https://user-images.githubusercontent.com/73281015/215402003-2c162cb1-5861-4718-a513-f7e2454d9be9.png)
