# GitHub and Command Line
In this lab report I replicated steps 4-9 from lab 7.

### Log into ieng6
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-1.png)
`ssh cs15lsp23gz@ieng-202.ucsd.edu`:
I typed the entire first line.

`<enter>` `<command> v` `<enter>`:
Then I pasted my password so I wouldn't have to type it out here.
This logged me into the remote server.

### Clone the fork of the repository
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-2.png)
`git clone` `<command> v` `<enter>`:
I typed the first part then pasted in the repository URL.
This cloned my fork of the lab7 repository to the remote server.

### Run the tests, show failure
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-3.png)
`cd la` `<tab>` `<enter>`:
I used tab because I was lazy.
This changed the working directory to the freshly copied one.

`bash te` `<tab>` `<enter>`:
Once again, I used tab to fill in the remaining text.
This ran the test.sh script, compiling and testing the appropriate files. It failed as expected.

### Edit ListExamples.java so the tests pass
The following screenshots are lines 40-50 of ListExamples.java open in vim.

To open vim:

`vim Li` `<tab>` `.java` `<enter>`:
The tab only auto-filled to ListExamples so I added the java extension myself.
This opened the file in vim.

Before:
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-vim-before.png)

To make this change:
`/change` `<enter>` `jll` `xi2` `<esc>` `:wq` `<enter>`:

`/change` `<enter>` made the cursor jump to the "c" in "change".

`jll` made the cursor move to the "1" in "index1".

`xi2` deleted the "1", entered insert mode, and typed a "2", making "index2".

`<esc>` returned to normal mode.

`:wq` `<enter>` saved and quit the file.

After:
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-vim-after.png)

### Run the tests, show success
(This image shows the result from the previous step)

![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-4.png)

`bash te` `<tab>` `<enter>`:
I used the same keystrokes as above.
This ran the test.sh script again, testing the appropriate files. 
This time it succeeded.

### Commit and push to GitHub
(Apologies for the large blank space. That was me figuring out the password/access token thing)

![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-5.png)
`git add Li` `<tab>` `.java` `<enter>`:
As used above, this autofilled to ListExamples and I added .java.
This added ListExamples.java to files that would be updated in the next commit.

`git status` `<enter>`:
All typed. This was to double check that the over worked.

`git commit -m "changed index1 to index2 on line 44"` `<enter>`:
All typed. This is committed with an appropriate update message.

`git push` `<command> v` `<enter>`:
I typed the first part and pasted in the URL again.
This pushed the changed files back to GitHub.
It prompted me to enter my username: `emivcleave` `<enter>`, again all typed.
Then it asked for a password, so I created an access token and pasted it here: `<command> v` `<enter>`.

### Success!
And to prove it worked I'm providing this screenshot too!
![Image](https://emivcleave.github.io/cse15l-lab-reports/LR4-6.png)
