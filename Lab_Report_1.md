# Lab Report 1
## Step 1: Installing VSCode
I was lucky in that I had VSCode already installed on my machine, appearing as below:
![Image](1)
Intalling VSCode is relatively strightforward by going to the VSCode website to download and install the applicaiton. Once a functioning VSCode installation is installed, it is time to start the remote access portion of the directions.
## Step 2: Remotely Connecting
First, open a terminal in VSCode. I, on Mac, used > Ctrl+Shift+\`
*One note for code commands: `$ ` shows the prompt, after which you (the user) must type the rest of the code for each step.*
Once inside the VSCode terminal, type `$ ssh cs15lsp23zz@ieng6.ucsd.edu` where the `zz` is replaced with the specific letters of your cse15l account. 
If this is the first time connecting to this host, there will be a message saying the authenticity of the host cannot be established, simply enter `yes`, but if on a later access date, somebody could be accessing or manipulating your connection in some way. You will then be asked for the password to your cse15l account. After the correct password, you should see a screen that looks something like this:
![Image](2)
The next step will assume you are still within the remote server (if you wish to leave the server, enter `q` or `exit` and you will be returned to the basic VSCode terminal).
## Step 3: Trying Some Commands
Now that you are within the remote server, you can play around with some commands. For testing the functionality, here are two very basic commands, showing the home directory:
![Image](3)
This is just one example of a command you can use in the server, and with that, you have entered a command in a remote server!

[1]: https://github.com/hdgehrke/cse15l-lab-reports/blob/main/Screen%20Shot%202023-04-06%20at%2018.18.07.png
[2]: https://github.com/hdgehrke/cse15l-lab-reports/blob/main/Screen%20Shot%202023-04-06%20at%2018.37.00.png
[3]: https://github.com/hdgehrke/cse15l-lab-reports/blob/main/Screen%20Shot%202023-04-06%20at%2018.41.09.png
