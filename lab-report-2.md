# Servers and Bugs
How to set up a server and test for bugs.

## Part 1: Servers
Below is the code for `StringServer` that concatenates a string in the query of the URL to the page on a new line.

I used the files included in the Wavelet folder (lab 2), including `Handler.class`, `Server.java`,  `ServerHttpHandler.class`, and `URLHandler.class`. 
However, `StringServer.java` is my file.

![Image](https://emivcleave.github.io/cse15l-lab-reports/code-lab-2.png)

### Examples
![Image](https://emivcleave.github.io/cse15l-lab-reports/message-1.png)
* The first two lines in the main method start a web server based on the command line argument.
The `handleRequest` method is called, which gets the string after the path `/add-message` and after the query `=`.
In `Handler`, the string is added to `returnString`, followed by a new line.
`returnString` is then returned, meaning all its contents are displayed on the webpage.
* In the first example, the phrase "Iced Americano" is the first input, so `Iced Americano` is first stored in `parameters[1]`, then in `returnString`. 
`Iced Americano` (with a new line after) is then displayed on the webpage.
  * Fun Fact! The `%20` in the URL represents a space: 32 is the ASCII character for a space, and 32 is 20 in hexadecimal.
  The percentage symbol is special in URLs too!
* In this case, `parameters[0]` will always be "s", because otherwise the webpage would produce an error message. 
Additionally, the path would remain "/add-message" and the separator for the parameters would be "=".

![Image](https://emivcleave.github.io/cse15l-lab-reports/message-2.png)
* Once the page is refreshed, `handleRequest` is revisited, with a new `url`. 
It once again pulls the query after `=`.
* The input `Emi :)` is the new `parameters[1]` and is added to `returnString`, followed by a new line. 
The new contents of `returnString` are as follows, which is then displayed on the webpage:

```
Iced Americano
Emi :)

```
* In this example, `url`, `parameters[1]`, and `returnString` are all changed.
While elements of the `Handler` class are changed, `Server.start` is only called once so nothing in the main method changes.

## Part 2: Bugs
The bug I chose for this section was the `averageWithoutLowest` method.

* Fail-inducing input:

```
@Test
  public void testAverageFail(){
    double[] arr = {2, 2, 4, 8, 10};
    assertEquals("6.0", "" + ArrayExamples.averageWithoutLowest(arr));
  }
```

* Pass-inducing input:

```
@Test
  public void testAveragePass(){
    double[] arr = {2, 4, 6, 8};
    assertEquals("6.0", "" + ArrayExamples.averageWithoutLowest(arr));
  }
```

* Symptom:

![Image](https://emivcleave.github.io/cse15l-lab-reports/bug1-lab-2.png)

* Fix:

```
// Before
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

```
// After
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    boolean skipped = false;
    for(double num: arr) {
      if(num != lowest || skipped == true) { sum += num; }
      else { skipped = true; }
    }
    return sum / (arr.length - 1);
  }
```

The error is that the original program would skip every value that is the same as the lowest value, which is an issue when the lowest value is repeated.
The fix is changing `skipped` to `true` when the lowest value has  been skipped and checking if the number isn't the lowest *or* if `skipped == true`.
This ensures that the lowest value is only skipped once, so it is counted if repeated.

## Part 3
The most notable things I learned were setting up the web server and actually using the terminal to use JUnit.
