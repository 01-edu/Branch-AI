## Exercise 9 Football tournament

The goal of this exercise is to learn to use permutations, complex

A Football tournament is organized in your city. There are 10 teams and the director of the tournaments wants you to create a first round as exciting as possible. To do so, you are allowed to choose the pairs. As a former data scientist, you implemented a model based on teams' current season performance. This models predicts the score difference between two teams. You used this algorithm to predict the score difference for every possible pair.
The matrix returned is a 2-dimensional array that contains in (i,j) the score difference between team i and j. The matrix is in  `model_forecasts.txt`.

Using this output, what are the pairs that will give the most interesting matches ?

If a team wins 7-1 the match is obviously less exciting than a match where the winner wins 2-1.
The criteria that corresponds to **the pairs that will give the most interesting matches** is **the pairs that minimize the sum of squared differences**

The expected output is:

```console
 [[m1_t1 m2_t1 m3_t1 m4_t1 m5_t1]
  [m1_t2 m2_t2 m3_t2 m4_t2 m5_t2]]

```

- m1_t1 stands for match1_team1
- m1_t1 plays against m1_t2 ...

**Usage of for loop is not allowed, you may need to use the library** `itertools` **to create permutations**

https://docs.python.org/3.9/library/itertools.html