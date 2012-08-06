# Semana 3

We explain the idea with a trivial example: suppose we need to write the value of $2\pi$ into a report; of course, we can directly write the number $6.28$. Now if I change my mind and I want $6\pi$ instead, I may have to find a calculator, erase the previous value and fill in the new one. Since it is extremely easy for the computer to calculate $6\pi$, why not leave this job to the computer completely and free the man of the labor work? What we need to do is to leave the source code in the document instead of a hard-coded value, and tell the computer how to find out the source code. Usually we use special markups for computer code in the source report, e.g. we can write `'the value is {% 6 * pi %}'`, in which `{%` and `%}` is a pair of marks that tell the computer `6 * pi` is source code and should be executed.

And here is a table created with the **xtable** package:

``` {r intro-table, results='asis'}
library(xtable)
xtable(head(mtcars[, 1:5]))
````

