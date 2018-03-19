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

11. Concatenate string
```matlab
s = strcat(s1,...,sN)
```

12. try...catch
```matlab
try

catch ME
    disp(ME.identifier);
    disp(ME.message);
    disp('Something is wrong.');
end
```

13. read string from csv file

    ``` matlab
    kernel_string = readtable('unique_kernelstring_.csv');
    ```

14. generate random numbers, non-repeat

    ```matlab
    randperm(n, k)
    ```

15. run  on server

    ```bash
    nohup matlab -nodisplay -nodesktop -nojvm -nosplash < YourCode.m & 
    ```

    ```bash
    nohup matlab -nojvm -nodisplay -nosplash -nodesktop < matlabscript.m 1>running.log 2>running.err &
    ```

    he -nodesktop starts MATLAB without bringing up the MATLAB desktop. **The JVM software is started**. Use the current window in the operating system to enter commands. * Will still work with graphics (you can use the plot commands)*

    -nodisplay: also starts the JVM and does not start the desktop in addition it also ignores Commands and the DISPLAY environment variable in LINUX. (will not work with graphics because of X limitations I presume)

    -nojvm does not start the JVM software and uses current window. Graphics will not work without the JVM

16. iterate struct

    ```matlab
    teststruct = struct('a',3,'b',5,'c',9)
    fields = fieldnames(teststruct)
    for fn=fields'
      fn
      %# since fn is a 1-by-1 cell array, you still need to index into it, unfortunately
      teststruct.(fn{1})
    end
    ```

17. shut down parallel pool

    ```matlab
    poolobj = gcp('nocreate');
    delete(poolobj);
    ```

    ​

