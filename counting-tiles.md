# Counting Tiles

Q. Count the **number of ways** to fill in an RxC grid with tiles of size 1x2 and 2x1.

![source: wikipedia](.gitbook/assets/image.png)

Solution: **781**

## Logic

Again, the solution can be divised by solving the grid row by row.

Let's think of a possible solution for a 4\*7 grid:

{% tabs %}
{% tab title="Plain Text" %}
```text
1 - - 1 - - 1
1 - - 1 1 1 1
- - - - 1 1 1
- - - - - - 1
```
{% endtab %}

{% tab title="4 tiles" %}
```
1 3 4 1 3 4 1
2 3 4 2 1 1 2
3 4 3 4 2 2 1
3 4 3 4 3 4 2

1 - top
2 - bottom

3 - left
4 - right
```
{% endtab %}
{% endtabs %}

Let `count(k, x)` denote the number of ways to construct a solution for rows 1...k and x is the 'string' of that row. \(such as "1341341"\)

There are 4 choices for each character, we have a maximum of 



## optimizations

