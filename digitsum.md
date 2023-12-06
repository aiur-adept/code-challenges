https://www.codewars.com/kata/59f6e1af3640ce12510000ad/train/javascript

```javascript
function findDigit(n) {
  /* 
  
  Initial survey:
  
    Consider the two sequences as A and B, "desequenced" as
  
          A': [1, 2, 3, 4, 5, 6, ...]
          B': [1, 4, 9, 16, 25, 36, ...]
    
    First, we need to find a formula for where 
  the breakpoints occur in A and B (as sequenced)
  - respectively -
  that way we can know,
  given an index, what integer and what square
  we are in given 'n'.
  
    Consider that for A', the number of digits in each
  "natural group" (1-9, 10-99, 100-999, ...) is given
  simply by 
  
          floor(log_10(n)) + 1
          
    In fact, this formula gives us the number of digits
  in any number, and thus can also be applied as part
  of the solution to natural group digit numbers in B.
          
  
  Intuition:
  
    The formula for the squares is more complicated,
  but can be deduced from observation. We should write
  some code to generate the sequence and see what
  pattern emerges. The code:
  
          const gl = (x) => Math.floor(Math.log(x)/Math.log(10)) + 1;
          for (let i = 1; i < 99; i++) { 
            console.log(`${i}, ${i*i}, ${gl(i*i)}`);
          }

    An even better way to explore is to deliberately track *when*
  the number of digits changes and figure out when those "breakpoints" occur:

          const gl = (x) => Math.floor(Math.log(x)/Math.log(10)) + 1;
          let current = 0;
          let until = 11;
          for (let i = 0; current < until; i++) {
            let ii = i + 1;
            let sq = i * i;
            let digits_i = gl(i*i);
            let digits_ii = gl(ii*ii);
            if (digits_ii !== current) {
              console.log(`transition:\n${i}, ${i*i}, ${gl(i*i)}`);
              console.log(`${ii}, ${ii*ii}, ${gl(ii*ii)}\n\n`);
              current = digits_ii;
            }
          }

    This turns out to be essentially a way to (inefficiently) compute
  sequence A017936, "smallest number whose square has n digits".

    The formula is

          Math.floor(10^(n-1)/2)
  */

  // that's enough for today
}
```
