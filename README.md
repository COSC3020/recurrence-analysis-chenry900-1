# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

the mystery function divides the array into thirds and is called 3 times giving you $3T(n/3)$. you have 2 nested for loops making the for loop run at $O(n^5)$. So the recurrance relation is $T(n) = 3T(n/3) + n^5$.The base case would be T(n) <= 1.

$T(n) = 3(3T(n/9) + (n/3)^5) + n^5$

$T(n) = 9T(n/9) + (n/3)^5 + n^5$

$T(n) = 9(3T(n/27) + (n/9)^5) + (n/3)^5 + n^5$

$T(n) = 3^i T(n/3^i) + ∑ (j = 0 to i - 1) (3^j / 3^{5j}) * n^5$

$n/3^i = 1$

so we let $i = log3n$

$T(n) = n * T(1) + n^5 * ∑ (j = 0 to log₃(n) - 1) (1 / 3^{4j})$

$n * 1 + ((n - 1) / 2) * n^5$

you can simplify all that to n + $n^5$

this proves that the recurrence relation is T(n) ∈ $O(n^5)$

I asked olivia from class and watched the lecture video then did it myself so the work is my own.
I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
