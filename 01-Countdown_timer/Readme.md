# Project-2
> For the 2nd Project, you will create a countdown timer.

# Step-by-Step Instructions

## Step-1
### Create a New file

 - Use the touch command to create a new file named countdown.sh in your project folder.
 - Give your file executable permissions so you can run it like the other one. It's the `chmod` commmand with the `+x` flag.
 - You want to use the `bash` interpreter again. Add a `shebang` at the top of your new file to denote that.
### Adding comments
 - Comments in `bash` look like this: `# <comment>`. Add a comment below the `shebang` that says `Program that counts down to zero from a given argument` so people know what it does. Note that the `shebang` is a special case and is not treated like a comment.
### Passing arguments
- Programs can take arguments. You can access them a few different ways with `$`. Add `echo $*` in your script to print all arguments passed to it
- Execute your script with `./countdown.sh`.
- Nothing was printed. Run your script again, but this time add three arguments to the command; `arg1`, `arg2`, and `arg3`. Place them after the command with a space before each one.
-`hint` Type `./countdown.sh` and press 'ENTER' output should be: ` arg1 arg2 arg3`
- `$*` printed all the arguments passed to your script. To access any one of them, use `$<number>.` `arg2` could have been accessed with `$2`. Change your script to `echo` the first argument instead of all the arguments.
- Run your file with `./countdown.sh arg1 arg2 arg3` again.
- Now it just prints the first argument. Your program will accept an argument to count down from. You will test it with an `if` statement to make sure it's a positive integer. I wonder what that syntax would look like. Type `help`  in the terminal to see if you can find anything. 
## Step-2
### if Commands
 -  Now it just prints the first argument. Your program will accept an argument to count down from. You will test it with an `if` statement to make sure it's a positive integer. I wonder what that syntax would look like. Type `help`  in the terminal to see if you can find anything. 
- This is a list of built-in commands. You should look over it, some of them may look familiar. I see `echo` in there. Another one is `if`. See if you can find out more about it by checking its `man` page.
- `Hint:` `man if`
- I guess there isn't a `man` page for it. At the top of the help screen, I noticed you can use `help <command>` to find out more. Yet another way to find out about a command 😥 See if you can find out more about if with that metho
- The syntax is at the top, not all of it is required. Here's another example:
	'''if [[ CONDITION ]]
		then
			STATEMENTS
	   fi'''
- Remove the `echo $1` in your script and add an `if` condition that checks `if [[ $1 == arg1 ]]`. In its `then` area, use `echo` to print `true` to the screen. There must be spaces on the inside of the brackets (`[[ ... ]]`)  and around the operator (`==`).
-  Make sure to remove the echo $1
- Notice that the end of the syntax is `fi` (`if` backwards).  It should print `true` if you pass `arg1` to your script now. Run the script with `arg1` as the only argument.
- The if condition worked, it printed true. Run it again with anything except arg1 as the first argument.
- Nothing was printed. One of the optional parts of if was an else area. You can use it like this:
	'''if [[ CONDITION ]]
		then
 			 STATEMENTS
		else
  			STATEMENTS
	    fi'''
- Add an `else` to your existing `if` condition. Use `echo` to print `false` if the condition fails.
- Run the script again and use anything except arg1 as the only argument. `hint` Type ./countdown.sh !arg1 in the terminal and press enter
- ./countdown.sh 10  # Replace 10 with the desired countdown duration.
- Now it printed false. Your program is expecting an integer to count down from as its argument. You can compare integers inside the brackets ([[ ... ]]) of your if with -eq (equal), -ne (not equal), -lt (less than), -le (less than or equal), -gt (greater than), -ge (greater than or equal). Change your if condition to check if your first argument is less than 5.
- It printed true since your argument was less than 5. Run it again with 5 as the argument.
- As expected, that printed false. Take a look at that help menu again. I want to see if we can find out more about how these expressions work.
- Near the top left, it says [[ expression ]]. Those look like the double brackets you are using. See if you can get more info about that with the help command like you did with help if.
- `hint` `help [[ expression ]]`
## Step-3
### 
