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
(image)
However, when I replace the variable `ListExamples` with the expected path `./student-submission/ListExamples.java`, it works.
(image)
(image)
I hope this is enough context to help me in this case. 
Thank you!

### TA Response
This seems to be an issue with how you referenced the variable `ListExamples`. Try reading this:
[https://algodaily.com/lessons/bash-commands-cheat-sheet1](https://algodaily.com/lessons/bash-commands-cheat-sheet1#:~:text=can%20also%20be%20used%20to%20output%20the%20values%20of%20system%20variables%20when%20preceded%20with%20a%20dollar%20sign%20($))

### Student Response
I fixed it! 
Thank you!
I forgot to add a `$` before the variable I wanted to reference, so the script thought I was literally referencing a file called `ListExamples`, and causing the error output.
(image)

### Process



## Part 2: Reflection


