# Lab Report 2
## Step 1: StringServer

Below is the code contained in my file `StringServer.java`, influenced by the template in `NumberServer.java`, the code given for Lab 2.

```
import java.io.IOException;
import java.net.URI;

class Handler1 implements URLHandler {
    String str = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return str;
        } else if (url.getPath().contains("add-message")) {
            String[] params = url.getQuery().split("=");
            if (params[0].equals("s")) {
                str += "\n";
                str += params[1];
                return str;
            }
            return "404 not found";
        }
        return "404 not found";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler1());
    }
}
```

Below are two instances of using `StringServer`, with different arguments.

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-24%20at%2022.26.41.png)

This URL calls `handleRequest`, with argument `http://localhost:4000/add-message?s=I'm doing quite well, thank you!`.
The operative field value `str` has the value `"\nHello\nHow are you"` before the call, and the value `"\nHello\nHow are you\nI'm doing quite well, thank you!"` after the call.

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-24%20at%2022.30.21.png)

Similarly, this URL calls `handleRequest`, with argument `http://localhost:4000/add-message?s=Ah! I should quite adore a light lunch with you, how does Wednesday sound?`.
The operative field value `str` has value `"\nHello\nHow are you\nI'm doing quite well, thank you!\nExcellent! I was hoping you could join me for lunch at some point this week, does this sound aggreeable to you?"` before the call. 
The value changes to `"\nHello\nHow are you\nI'm doing quite well, thank you!\nExcellent! I was hoping you could join me for lunch at some point this week, does this sound aggreeable to you?\nAh! I should quite adore a light lunch with you, how does Wednesday sound?"` after the call.

## Step 2: Buggy Code

For this part, I selected the `reversed(int[] arr)` method from `ArrayExamples.java`. Before changes, the code looked like this:

```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Of these tests, `testReversed()` shows a non-failure-inducing input, while `testReversed2()` shows a failure-inducing input.

```
  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }

  @Test
  public void testReversed2() {
    int[] input1 = {1, 2, 3};
    assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input1));
  }
```

Results of running the tests are shown in the following image:

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-24%20at%2023.26.47.png)

The following code block shows the `reversed(int[] arr)` method after fixing the bugs:

```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

And an image showing it passing the two tests:

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-24%20at%2023.33.37.png)

This fix addresses the issue through two changes. Firstly, the order of the assignment operation within the `for` loop is reversed, so that `newArray` is populated with elements from `arr`. Next, `newArray` is actually returned, giving the reverse of `arr`.

## Step 3: Learning?

I think the main thing I learned was how a server works. I knew roughly what the parts of a url were before the lab, but I didn't really know how programs took that information and did anything with it.
I certainly didn't think one could do operations like concatenate a string entered as an argument quite so easily. I was under the impression that the process was something incredibly intensive, 
and even though we did have the help of `Server.java`, the whole process was very straightforward. 


