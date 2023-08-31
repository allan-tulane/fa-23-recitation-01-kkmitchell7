[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11680964&assignment_repo_type=AssignmentRepo)
# CMPS 2200  Recitation 01

**Name (Team Member 1):**_________________________  
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

The worst case input value for both linear_search and binary_search is that the key is not in the list so each must continue searching as long as possible until they conclude that it must not be in the list.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

The best case input for linear_search is that the key is in the first index since that's the very first place it searches. It would find it immidiately and end the process. Similarly, binary_search's best case input is the first place it looks, but since binary search starts by looking at the middle of the list, the middle is the best case input for the key.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:


|     n |   linear |   binary |
|-------|----------|----------|
|    10 |    0.007 |    0.003 |
|   100 |    0.003 |    0.004 |
|  1000 |    0.034 |    0.003 |
| 10000 |    0.363 |    0.006 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

For the linear search it seems that the time is O(n) because as we add 0s to 10, the time similarly increases by a decimal place. There's something weird going on with n = 100, though and I'm not sure why the time would be less than n = 10. I think this could be due to a bug in my code or because the machine can't get specific enough for the minute differences in run times between 10 and 100.
For the binary search I think it matches the O(logn) runtime because its about increasing by 0.001 ms per every 0 added to 10. Without graphing all my data, I get the sense that its following this theoretical run time with some room for error.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? - k * O(n)
  + For binary search? Theta(n^2) + k * O(logn)
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? - There are no values of k where it's always more efficient to first sort and then use binary search because when the x values get large enough the k * O(n) will always intersect. n^2 + k * logn has an asymptote of x = 0, so it just gets less and less efficient with bigger values of x.
