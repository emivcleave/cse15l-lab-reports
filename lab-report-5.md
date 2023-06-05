# Debugging
In this lab report, I created a mock interaction between a student and tutor that involves debugging.

## Part 1: Debugging Scenario
### Student Question
**What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?**

I'm using a MacBook Pro and the VSCode built-in terminal.

**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.**

I decided to practice for the upcoming skill demo, but I'm stuck on step 8, which is to fix the grading script to look inside other directories for the correct file.
I didn't expect `ListExamples.java not found, Score: 0/4` because I think I fixed the issue.

**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**

I replaced all instances of `student-submission/ListExamples.java` with the variable `ListExamples` which is the output for the command `find . -name ListExamples.java`.
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR5-1.png)
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR5-2.png)

However, when I replace the variable `ListExamples` with the expected path `./student-submission/ListExamples.java` (from the last line in the above image), it works.
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR5-3.png)

I hope this is enough context to help me in this case. 
Thank you!

### TA Response
This seems to be an issue with how you referenced the variable `ListExamples`. Try reading this:
[https://algodaily.com/lessons/bash-commands-cheat-sheet1](https://algodaily.com/lessons/bash-commands-cheat-sheet1#:~:text=can%20also%20be%20used%20to%20output%20the%20values%20of%20system%20variables%20when%20preceded%20with%20a%20dollar%20sign%20($)).
How does what you typed differ from the contents of this article?

### Student Response
I fixed it! 
Thank you!
I forgot to add a `$` before the variable I wanted to reference, so the script thought I was literally referencing a file called `ListExamples`, and causing the error output.
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR5-4.png)

### Process
First, I cloned the autograder repository, [https://github.com/ucsd-cse15l-s23/grader-skill-demo2](https://github.com/ucsd-cse15l-s23/grader-skill-demo2). 
Then, I cd'ed to the `grader-skill-demo2` directory.

I changed the contents of `grade.sh`, where I added `ListExamples=$(find . -name ListExamples.java)` at line 11, and changed the instances of `student-submission/ListExamples.java` originally on lines 11 and 20 to be `ListExamples`.

After that, I ran `bash grade.sh https://github.com/ucsd-cse15l-s23/list-methods-corrected` to trigger the bug.
To demonstrate that it was the `$` and not a separate error, I replaced the `ListExamples` with `./student-submission/ListExamples.java` and ran it again with the same command.

To fix the bug, I reverted to the ListExamples version, and added a `$` in front of `ListExamples` so it would be read as a variable.

## Part 2: Reflection
I thought the lab tasks from week 7 and subsequent lab report 4 tasks were pretty fun.
Maneuvering vim was a little bit difficult, but once I figured it out opening files in vim and messing around/messing things up was really entertaining!
I remember getting a little frusterated at first, but then finding out the shortcuts to make things faster felt very worth it.

This isn't anything specific but I had fun with the lab 9 tasks as well and I even finished early whereas with the previous labs I didn't even get through all the tasks.
That made me feel very accomplished and a sense of advancement which was very cool to feel.
