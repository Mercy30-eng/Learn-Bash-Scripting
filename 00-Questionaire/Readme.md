# Project -1
> In this project, you'll learn bash scripting by creating a small program called 'questionnaire'.

## Step-by-Step Tutorial
>You can run commands in the terminal or put them in a file to be run as a script. 
### Step-1
	- Use the `touch` command to create `questionnaire.sh` in your project folder.
	- To start open the file in a text editor of your choice vim or emacs and add the text `echo hello questionnaire`.
### Step-2
	- Your script has one command. Run it with `sh questionnaire.sh` to see what happens. sh stands for shell.
	- Using sh to run your script uses the shell interpreter. Run your script again with `bash questionnaire.sh` o use the bash
          interpreter.
	- The output was the same. There are many interpreters which may not give the output you expect. Find out where the `bash` interpreter is located by entering `which bash` in the terminal. 
### Step-3
	- That's the absolute path to the `bash` interpreter. You can tell your program to use it by placing a shebang at the very top of the file like this: `#!<path_to_interpreter>`. Add a `shebang` at the very top of your file, the one you want looks like this:` #!/bin/bash`.
### Step-4
	- Now, instead of using `sh` or `bash` to run your script. You can run it by executing the file and it will default to bash. 	      Execute your script with `./questionnaire.sh`. You will get a permission denied error.
 	- You should have got a permission denied message because you don't have permissions to execute the script. List what's in           the `project` folder in long list format with `ls -l` to see the file permissions.
### Step-5
	- Next to your file is `-rw-r--r--`.All but the first character `(-)`  describe permissions different users have with the
           file.`r` means `read`, `w` means `write`, `x` means `execute`. I don't see an `x` anywhere, so nobody can execute it. Enter `chmod +x questionnaire.sh` to give everyone executable permissions.
	- List what's in the folder again with `ls -l` to see the new persmissions.
	- The `x` was  added by each type of user to denote that anyone can execute the file. Run your file again by executing it with `./questionnaire.sh`.
	- Now it works. In your script, you can add any commands that you would be able to enter in the terminal. Test this by adding the `ls -l`  command below your other command. i.e Add `ls -l` at the bottom of your `questionnaire.sh` file.
	- Run the script by executing it again.
### Step-6
	- Your script printed the result of the two commands as if you entered them in the terminal. Delete everything but the shebang from your file so you can start making the questionnaire.
	- Bash has variables, functions, and other things you might be familiar with. You can create a variable with `VARIABLE_NAME=VALUE`. There cannot be any spaces around the equal (`=`) sign. If a variable has any spaces in it, place double quotes around it. Create a variable named `QUESTION1` and set it's value to `"What's your name?"`.
	- To use a variable, place $ in front of it like this: $VARIABLE_NAME. Shell scripts run from top to bottom, so you can only use variable below where it's created. Use echo to print your variable.
	- Run the file like you did before to see if it worked.
### Step-7
	- The question was printed. Next, you want to be able to accept input from a user. You can do that with read like this: read VARIABLE_NAME. This will get user input and store it into a new variable. After you print the question, use read to get input and store it in a variable named NAME.
   	- At the bottom of your script, use echo to print Hello <name>. to the terminal.
	- Don't forget the period
	- Run the file again. Type your name and press enter after it asks for it.
### Step-8 
	- Right below your first variable, create another one named QUESTION2. Set the value to, Where are you from?. Make sure to put it in double quotes.
	- After your read command, use your new variable to print the next question.
	- Below where the second question is printed, use read to get input from the user into a variable named LOCATION.
	- Run the script and enter values when it is waiting for input.
### Step-9
	- It's looking good. I want a title to appear when the program first starts. Use echo to print ~~ Questionnaire ~~ before anything else is printed.
	- Run the script and enter values until it is done again so you can see what the title looks like.
	- It would be nice if there was some empty lines around the title. You've probably used the --help flag before, see if you can use it with echo to try and find a way to add empty lines.
	- That didn't work as I hoped. Another way to find information about a command is with man. It stands for manual and you can use it like this: man <command>. See if there's a manual for echo.
	- At the top of the menu, the -e option looks promising. And the \n below it says new line. You should take a look at those. In your script, change the title to echo -e \n~~ Questionnaire ~~\n to see if that prints the empty lines.
	- Run it to see if it worked. You can press ctrl+c to close the program after it starts if you don't want to enter values.
	- It didn't print the empty lines. echo will only print empty lines if the value is enclosed in quotes. Place double quotes around the title that gets printed to see if it works.
	- Run your script again to see if that fixed it.
### Step-10 
	- Now it's working 😄 Create a QUESTION3 variable next to the other two, set it's value to "What's your favorite coding website?"
	- Use echo to print the third question after you read the LOCATION.
	- After the question you just printed, add code to read input into a variable named WEBSITE.
	- Change the echo command of the response to print this sentence instead: Hello <name> from <location>. I learned that your favorite coding website is <website>!.
	- Run the script and enter values when the program is waiting. Let's see the final output.
	- One last thing. Change that final response to print an empty line at the beginning of the sentence.Don't forget to put the response in double quotes so it prints the empty line
	- Run it one last time and enter values when it asks to see if you like how it looks.
### Step-11
	- It looks good. I think you are done with this script for now.

