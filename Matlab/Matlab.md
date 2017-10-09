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

3\. C `= setxor(A,B)` 

returns the data of `A` and `B` that are not in their intersection (the symmetric difference), with no repetitions. That is, `setxor` returns the data that occurs in `A` or `B`, but not both. `C` is in sorted order.

