

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

Vector to triangular matrix:

```matlab
B = triu(ones(4));
B(B==1) = A;
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

15. iterate struct

    ```matlab
    teststruct = struct('a',3,'b',5,'c',9)
    fields = fieldnames(teststruct)
    for fn=fields'
      fn
      %# since fn is a 1-by-1 cell array, you still need to index into it, unfortunately
      teststruct.(fn{1})
    end
    ```

16. shut down parallel pool

    ```matlab
    poolobj = gcp('nocreate');
    delete(poolobj);
    ```

17. length of each string in a cell array

    ```matlab
    cellfun(@length,A)
    ```

18. save all the variable if there is an error

    ```matlab
    dbstop if error
    ```

19. set number between 1 and 3 to zero

    ```matlab
    array(and(array>1,array<3))=0
    ```


21. Plot

    另一个重要的技巧是delete/clf-plot-pause
    用plot可以画图（注意记录句柄），然后用delete删掉特定图象，或用clf清图，再绘制，这可以在figure窗口产生动画。但是如果只plot，往往只会在全部程序执行结束时显示，这时候需要用pause让figure完成图像的更新。drawnow貌似也可以，但是我比较喜欢用pause，能够简单地控制动画的速度。
    这会方便调试和展示。这个技巧尤其适合使用matlab的图形用户界面设计功能时构造一个显示运行状态等信息的figure。

22. Shortcuts

    Esc :clear line in command window

    Ctrl+left arrow: move cursor to the left word      

23. Matlab plot

    ```matlab
    %set ticks
    x=[0 5 10];
    labels={'x = 0','x = 5','x = 10'}
    set(gca,'xTick',x,'xTickLabel',labels)
    %set font size
    xt = get(gca, 'XTick');
    set(gca, 'FontSize', 16)
    %axes and legend font size
    set(gca,'fontsize',20)
    
    xlabel('percentage','FontSize',18)
    %set position
    set(gcf, 'Position', [0, 0, 800, 600])
    set(gcf, 'Units', 'Normalized', 'OuterPosition', [0 0 0.5 0.5]);
    %____________________________________
    
    %use one title even with subplots
    h=figure;
    h.NextPlot = 'add';
    a = axes; 
    	%// Set the title and get the handle to it
    ht = title('Test');
    	%// Turn the visibility of the axes off
    a.Visible = 'off';
    	%// Turn the visibility of the title on
    ht.Visible = 'on';
    
    % linewidth_________________________
    plot(x, 'MarkerSize',3,'LineWidth',2);
    % 用右边的y轴展示
    yyaxis right 
    % get color
    p=plot(X,y);
    c=p.Color;
    %save figure
    print('image','-dpng')
    
    %Use Screen Size and Resolution
    fig = gcf;
    fig.PaperPositionMode = 'auto';
    print(filename,'-dpng','-r0')
    
    %legend Outside 
    h=legend('Line 1','Line 2','Location','NorthEastOutside')
    
    %transparent line
    p=plot(X,y)
    p.Color(4)=0.5
    ```

24. matlab save table to csv

    ``` matlab
    array2table(nlml_samples,'VariableNames',names);
    writetable(T,filename)
    ```


25. find string in cell

    ```matlab
    find(strcmp(newstr,all_str))
    ```

26. find in string

    ```matlab
    ~isempty(strfind(str,'('))
    ```

27. inverse

    ```matlab
    Replace inv(A)*b with A\b
    Replace b*inv(A) with b/A
    ```


