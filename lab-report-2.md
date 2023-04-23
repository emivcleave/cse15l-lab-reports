# Servers and Bugs
How to set up a server and test for bugs.

## Part 1: Servers
Below is the code for `StringServer` that concatenates a string in the query of the URL to the page on a new line.

I used the imports from the Wavelet folder (lab 2), including `Handler.class`, `Server.java`,  `ServerHttpHandler.class`, and `URLHandler.class`.
![Image](https://emivcleave.github.io/cse15l-lab-reports/code-lab-2.png)

### Examples
![Image](https://emivcleave.github.io/cse15l-lab-reports/message-1.png)
* The first two lines in the main method start a web server based on the command line argument.
The `handleRequest` method is called, which gets the string after the path `/add-message` and after the query `=`.
In `Handler`, the string is added to `returnString`, followed by a new line.
`returnString` is then returned, meaning all its contents are displayed on the webpage.
* In the first example, the phrase "Iced Americano" is the first input, so `Iced Americano` is first stored in `parameters[1]`, then in `returnString`. 
  * The `%20` in the URL represents a space: 32 is the ASCII character for a space, and 32 is 20 in hexadecimal.
"Iced Americano" is then displayed on the webpage.
* In this case, `parameters[0]` will always be "s", because otherwise the webpage would produce an error message.

![Image](https://emivcleave.github.io/cse15l-lab-reports/message-2.png)
* Once the page is refreshed, `handleRequest` is revisited, with a new `url`. 
It once again pulls the query after `=`.
* The input `Emi :)` is the new `parameters[1]` and is added to `returnString`, followed by a new line.
The new contents of `returnString` are as follows, which is then displayed on the webpage:

```
Iced Americano
Emi :)

```
* In this example, `url`, `parameters[0]` and `returnString` are all changed.
