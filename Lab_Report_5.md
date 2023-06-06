# Lab Report 5
## EdStem post

Post content:

"I am using MacOS, and am on VSCode."

"I expected to have my code pass my tests, but it appears to print too many failure messages. I expect one message, but get three."
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screenshot%202023-06-05%20at%2018.23.08.png)

Code: 
script.sh:
```
echo Beginning testing...
cd Java/
javac *.java
java Foo 1> output.txt
count=`grep -c "Dye failed!" output.txt`
echo Expected dye failures: 1
echo Actual dye failures: $count
if [[ $count != 1 ]]
then
    echo Code failed!
else
    echo Code succeeded!
fi
echo Finished testing!
cd ..
```
Foo.java:
```
public class Foo {
    public static void main(String[] args) {
        System.out.println("Hello World");
        Tshirt shirt1 = new Tshirt(10, "mauve");
        System.out.println("Expected value: white, actual: " + shirt1.color);
        shirt1.dye("blue"); // Should succeed
        shirt1.dye("turqoise"); // Should fail
        shirt1.dye("purple"); // Should succeed
        System.out.println("Expected value: purple, actual: " + shirt1.color);
    }
}
```
Tshirt.java:
```
public class Tshirt {
    boolean dyed;
    int size;
    String color;
    String[] allowedColors = {"white", "black", "red", "blue", "purple",
                                "green", "pink", "grey", "orange"};

    public Tshirt(int size, String color) {
        if (size < 1) throw new IllegalArgumentException();
        this.size = size;
        this.dyed = false;
        this.color = "white"; // base value
        for (String s: this.allowedColors) {
            if (color.equals(s)) { this.color = color; }
        }
    }

    public void dye(String color) {
        for (String s: this.allowedColors) {
            if (color.equals(s)) {
                this.color = color;
                this.dyed = true;
            }
        }
        System.out.println("Dye failed!");
    }
}
```
"My code in `Foo.java` should run some tests, giving the desired results, and `script.sh` runs that file. 
I just can't tell where the bug is. The java files are in the `Java/` directory."

## TA Response

"Examine the `dye` method carefully, try adding print statements to check the behavior of the `dyed` field or the `color` field.
What is the desired behavior of the `for` loop?"

## Student retry

Adding a print statement within the `if` statement, combined with further analysis, revealed that the bug was caused by a missing early return within the `if` block.
```
public class Tshirt {
    boolean dyed;
    int size;
    String color;
    String[] allowedColors = {"white", "black", "red", "blue", "purple",
                                "green", "pink", "grey", "orange"};

    public Tshirt(int size, String color) {
        if (size < 1) throw new IllegalArgumentException();
        this.size = size;
        this.dyed = false;
        this.color = "white"; // base value
        for (String s: this.allowedColors) {
            if (color.equals(s)) { this.color = color; }
        }
    }

    public void dye(String color) {
        for (String s: this.allowedColors) {
            if (color.equals(s)) {
                this.color = color;
                this.dyed = true;
                System.out.println("Successfully dyed");
            }
        }
        System.out.println("Dye failed!");
    }
}
```
Produced the following in the `output.txt` file:
```
Hello World
Expected value: white, actual: white
Successfully dyed
Dye failed!
Dye failed!
Successfully dyed
Dye failed!
Expected value: purple, actual: purple
```

After fix:
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screenshot%202023-06-05%20at%2018.34.22.png)

## Final Code
Before:
```
public class Tshirt {
    boolean dyed;
    int size;
    String color;
    String[] allowedColors = {"white", "black", "red", "blue", "purple",
                                "green", "pink", "grey", "orange"};

    public Tshirt(int size, String color) {
        if (size < 1) throw new IllegalArgumentException();
        this.size = size;
        this.dyed = false;
        this.color = "white"; // base value
        for (String s: this.allowedColors) {
            if (color.equals(s)) { this.color = color; }
        }
    }

    public void dye(String color) {
        for (String s: this.allowedColors) {
            if (color.equals(s)) {
                this.color = color;
                this.dyed = true;
            }
        }
        System.out.println("Dye failed!");
    }
}
```
Only `Tshirt.java` was changed, by adding an early return within the `if` statement to exit after a successful dying:
```
public class Tshirt {
    boolean dyed;
    int size;
    String color;
    String[] allowedColors = {"white", "black", "red", "blue", "purple",
                                "green", "pink", "grey", "orange"};

    public Tshirt(int size, String color) {
        if (size < 1) throw new IllegalArgumentException();
        this.size = size;
        this.dyed = false;
        this.color = "white"; // base value
        for (String s: this.allowedColors) {
            if (color.equals(s)) { this.color = color; }
        }
    }

    public void dye(String color) {
        for (String s: this.allowedColors) {
            if (color.equals(s)) {
                this.color = color;
                this.dyed = true;
                return;
            }
        }
        System.out.println("Dye failed!");
    }
}
```

## Part 2:
One thing I learned that I really did not expect to learn was how to run code and access a remote server (ieng6). 
I sort of knew that servers were a thing that existed before this class, but the extent of cloning git repos and editing files with vim remotely really blew my mind. 
The first half of the quarter had local server information that I also found cool, but the scope of my server knowledge really expanded through the second half of the course.
I also had to troubleshoot some annoying filesystem issues that solidified my understanding of how paths and directories work and their relation to written code. 
While the second half content has been more difficult, I think it has been very interesting and in depth. 
