# Lab Report 1
## Step 1: Installing VSCode
I was lucky in that I had VSCode already installed on my machine, appearing as below:

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-06%20at%2018.18.07.png)

Intalling VSCode is relatively strightforward by going to the VSCode website to download and install the applicaiton. Once a functioning VSCode installation is installed, it is time to start the remote access portion of the directions.
## Step 2: Remotely Connecting
First, open a terminal in VSCode. I, on Mac, used > Ctrl+Shift+\`
*One note for code commands: `$ ` shows the prompt, after which you (the user) must type the rest of the code for each step.*
Once inside the VSCode terminal, type `$ ssh cs15lsp23zz@ieng6.ucsd.edu` where the `zz` is replaced with the specific letters of your cse15l account. 
If this is the first time connecting to this host, there will be a message saying the authenticity of the host cannot be established, simply enter `yes`, but if on a later access date, somebody could be accessing or manipulating your connection in some way. You will then be asked for the password to your cse15l account. After the correct password, you should see a screen that looks something like this:

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-06%20at%2018.37.00.png)

The next step will assume you are still within the remote server (if you wish to leave the server, enter `q` or `exit` and you will be returned to the basic VSCode terminal).
## Step 3: Trying Some Commands
Now that you are within the remote server, you can play around with some commands. For testing the functionality, here are two very basic commands, showing the home directory:

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-06%20at%2018.41.09.png)

And here are some more commands with more information about the server contained:

![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-04-24%20at%2020.41.55.png)

`$ ls -a` lists all the files and folders in the current directory, including some files starting with a `.`. Notably, one file is `hello.txt`, whose contents can be printed with `$ cat hello.txt` But since it is a file and not a folder, changing directory to `hello.txt` gives an error as no such directory exists.

These are just a few examples of commands you can use in the server, and with that, you have entered commands in a remote server!

[1]: https://github.com/hdgehrke/cse15l-lab-reports/blob/main/Screen%20Shot%202023-04-06%20at%2018.18.07.png
[2]: https://github.com/hdgehrke/cse15l-lab-reports/blob/main/Screen%20Shot%202023-04-06%20at%2018.37.00.png
