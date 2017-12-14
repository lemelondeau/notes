1\. Transfer a triangular matrix to vector:

```matlab
%get the upper tri of B
B=randn(n);
A=ones(n);
A_tril=tril(A);%lower tri
index=find(A_tril==0);
B_tri_vec=B(index);
```

```matlab
tril(ones(4,4),-1)

ans =

    0    0    0    0
    1    0    0    0
    1    1    0    0
    1    1    1    0
```

```matlab
triu(ones(4,4),-1)

ans = 

    1    1    1    1
    1    1    1    1
    0    1    1    1
    0    0    1    1
```

2\. Get random non-repeat integer

```matlab
randperm(10,5)

ans =

     9     8     1     7     3

```

3\. C = setxor(A,B)

returns the data of `A` and `B` that are not in their intersection (the symmetric difference), with no repetitions. That is, `setxor` returns the data that occurs in `A` or `B`, but not both. `C` is in sorted order.

4\. Add path:
```matlab
addpath('mypath');
%add all subfolders
addpath(genpath('mypath'));
```

5\. Pairwise distance between two sets of observations
```matlab
%row by row distance
D=pdist(X,Y)
```

6\. Generate random numbers that are repeatable
```matlab
%initialize
rng('default');
%seed of 1
rng(1);
%save the generator settings
s=rng;
%recover
rng(s);
```

7. Find given row in a matrix

```matlab
% find all, also faster
index = find(all(bsxfun(@eq, M, X), 2));

% find the first row
ismember(X, M, 'rows')
```

8. return statistics

``` matlab
%return chi-square, contengency table, p-value
crosstab(X, Y);
```

9. Count elements in an array
```matlab
numbers=unique(v);       %list of elements
count=hist(v,numbers);   %provides a count of each element's occurrence
```
```matlab
% another way
length(find(v==num));
```

10. Read data from csv

    ```matlab
    % read all, the file must contain only numeric values
    M = csvread(filename)
    % read data from the file starting at row offset R1 and column offset C1
    M = csvread(filename, R1,C1)
    ```

    ​