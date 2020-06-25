---
description: AKA Levenshtein distance.
---

# Edit Distance

## Question

What is the _edit distance_ between `LOVE` and `MOVIE` ?

Operations allowed are:

* insert
* remove
* modify

## Logic

Given

String `x` of size `n`  
String `y` of size `m`

Find the minimum number of edits so that x == y.

**Recursively thinking,** the distance between "LOVE" and "MOVIE" is either

* distance\("LOVE", "MOVI"\) + 1 OR
* distance\("LOV", "MOVIE"\) +  1 OR
* distance\("LOV", "MOVI"\) + \(**1 OR 0\)**

For example, if distance\("LOVE", "MOVI"\) is 2 — which it is — then the distance\("LOVE", "MOVIE"\) is 3, since we only need to _insert_ once. We simply do this for each of the 3 operations.

Now instead of saying `dist("LOVE", "MOVIE")`, let's just say `dist(3, 4)`where parameters are the last index of the prefix. Then we can formulate:

```cpp
dist(a, b) = min(
			dist(a, b-1) + 1,
			dist(a-1, b) + 1,
			dist(a-1, b-1) + cost(a, b)
		)
```

* `cost(a, b)` is 0 if x\[a\] == y\[b\].  For example, if dist\("LOV", "MOV"\) is 1, then dist\("LOVE", "MOVE"\) is also 1.

## Implementation

{% tabs %}
{% tab title="Step 1" %}
```text
First we use dynamic programming 
to populate the following table:

(Finish this table as an exercise)

0 1 2 3 4 5 
1 1 2 3 4 5 
2 2 1 - - - 
3 - - - - - 
4 - - - - - 
```
{% endtab %}

{% tab title="Step 2" %}
```
0 1 2 3 4 5 
1 1 2 3 4 5 
2 2 1 2 3 4 
3 3 2 1 2 3 
4 4 3 2 2 2 
```
{% endtab %}

{% tab title="Step 3" %}
```
Optionally you can identify the minimum path

0
  1
    1
      1 2
          2
```
{% endtab %}
{% endtabs %}

## Code

```cpp
for(int i=1; i<n; i++) {
    for(int j=1; j<m; j++) {
        if (x[i] == y[j])
            dp[i][j] = dp[i-1][j-1];
        else
            dp[i][j] = 1 + min(
                dp[i-1][j], // insert
                dp[i][j-1], // remove
                dp[i-1][j-1]// replace
            );
    }
}
```

Entire Code: [https://ideone.com/KM0t3U](https://ideone.com/KM0t3U)

