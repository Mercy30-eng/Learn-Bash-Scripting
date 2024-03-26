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
- It might not be a bad idea to read that. Looks like you can use some, probably familiar, things like !, &&, and || to compare multiple expressions. There's also == and != operators for an individual expression. It says something about the test built-in command.  - See if you can bring up the help menu for that.
- At the top are some file operators. There's some string and other operators as well. You should take a look at them. Near the bottom, are the arithmetic operators you used with your if condition. Change the condition in your script to check if the first argument is less than or equal to 5.
- Run the script and use 5 as a first argument again
- Now it prints `true`. Remember I said any command can run in the terminal or a script. Try running an expression right in the terminal by entering `[[ 4 -le 5 ]]` in it.
- Nothing happened? Each command has an exit status that can be accessed with $?. View the exit status of the last command with echo $?.
- The exit status of `0` means it was true, `4` is indeed less or equal to `5`. Try it again with `[[ 4 -ge 5 ]]`.
- Use `echo` to view the exit status of the command you just entered.
- It printed 1 this time for false. You can separate commands on a single line with ;. Enter your last two commands on one line like this:` [[ 4 -ge 5 ]]; echo $?`. It will run the expression, then print the exit status of it since it was the last command.
- You can think of an exit status of 0 as true. But it means that the command had zero errors. All commands have an exit status. Using the same syntax, enter `bad_command;` and check its exit status on a single line.
- `command not found`, with an exit status of `127`. Anything but `0` means there was an error with the command. `bad_command` didn't exist. Try it again with `ls`.
- The command executed as expected and there were zero errors. So it gave you an exit status of `0`. Try it again with  `ls -y`.
- The `-y` flag doesn't work with `ls` so it gave you an exit status other than `0`, meaning that the command was unsuccessful. View the `help` menu of the `test` command again, I want to see what else is in that list.
- You tried a few of the arithmetic operators, those work for integers. Try one of the file operators. The first one on the list checks if a file exists. Type `[[ -a countdown.sh ]]; echo $?` in the terminal to see if your file exists.
- The file must exist. It's checking the folder the command is entered from. Try it again with `bad_file.txt`.
- `bad_file.txt` doesn't exist. I think you're getting the hang of this. Using the same syntax, check if you have permissions to execute your `countdown.sh` file. You may want to look at that menu again.
- You played around with a number of the expressions. View the `help [[ expression ]]` menu again that you looked at before to see a few more options. You can view the menu with just `help [[`.
- As I mentioned before, you can test multiple expressions with `&&` and `||`. Enter `[[ -x countdown.sh && 5 -le 4 ]]; echo $?` in the terminal to test the file is executable by you **and** five is less than or equal to four.
- Both conditions weren't true, so the exit status was `1` for `false`. Try testing the same two conditions with the `or` operator.
- One of the conditions was true so it printed `0`. I think that's enough of a detour. Back in your script, change the `if` condition to check if the first argument is **greater than zero** so you can be sure it's something you can count down from.
- The condition you added checks if a positive integer was passed as an argument to the script and executes the `then` area. Change the existing `echo` command to print `Include a positive integer as the first argument.` if a positive integer is not used.
- Run your script and use `1` as a first argument to make sure the condition is working.
- Run it again and use anything but a positive integer as the only argument.
- Looks like your `if` condition is working. Next, you want to loop over the argument and count down to zero from it. Check the `help` menu to see if there's any commands for this.

## Step-3 
### For-Loop

- There's two `for` loops in there, you want the second one. Here's an example:

```sh
for (( i = 10; i > 0; i-- ))
do
  echo $i
done
```

The above creates a variable (`i = 10`), then prints it, subtracts one, and repeats until `i` is not greater than `0`. So it prints `10` through `1`. In the `then` area of your condition, replace the `echo` with a `for` loop that prints from the argument (`$1`) to `1`.
- Run your script and use `10` as the first argument.
- It works :smile: But I want it to pause for one second between each number. Check the `help` menu again to see if there's any commands that might help.
- I'm not seeing the command I was hoping to. These are the built-in commands, where are the rest? Type `ls /` to look around.
- The `/` listed what's in the root of the file system. I see a `bin` folder, `bin` stands for `binary`. View what's in it with `ls /bin`.
- These are some non built-in commands. There's quite a few that should look familiar. One is `bash`, that's the one you used for the `shebang` in your scripts. I see one called `sleep`. View the manual of it.
- At the top, it says you can pause execution for a number of seconds. Try it out by entering `sleep 3` in the terminal.
- That should work. In your `for` loop, use `sleep` to make the script pause for `1` second after each number is printed.
- Run your script and use 3 as the first argument.
- Awesome. Except it should print `0` instead of stopping at `1`. Change the condition in your for loop so that it checks for `i >= 0`
- Run your script with 3 as the argument again.
- Excellent. I want it to display a title like the other script. Make it so that it prints `~~ Countdown Timer ~~` before anything else. Include a new line before and after it like you did for the other title.
- Run your script and use `1` as the first argument again to see the title.
- This is fun. You can create a multiline comment like this:

```sh
: '
  comment here
  more comment here
'
```

Comment out your `for` loop with a multiline comment. I want to try and do this with a `while` loop.
- View the `help` menu for the `while` command to see if you can find anything.
- It shows the syntax. First, below your comment, create a variable named `I` that is set to the value of your first argument. It will start there, then on each iteration of the `while` loop you can subtract `1` from it until it reaches `0`.
- The menu showed that you can make a `while` loop like this:

```sh
while [[ CONDITION ]]
do
  STATEMENTS
done
```

Add a `while` loop below the `I` variable you made. The condition should be `$I -ge 0` and you should `echo` the `I` variable in the `do` statements.
- `I` never changes here, so you would have an infinite loop. You can subtract one from `I` with double parenthesis (`((...))`) and the `--` operator. In your while loop, add `(( I-- ))` after you `echo $I` to subtract one from `I` on each pass. 
- 
The last thing to do is to add the `sleep` again. In your `while` loop, add the code to make it `sleep` for `1` second. Add the code after the `(( I-- ))`.

#### HINTS

- Use the same `sleep 1` you used in the `for` loop
- Your `while` loop should look like this:
```sh
while [[ $I -ge 0 ]]
do
  echo $I
  (( I-- ))
  sleep 1
done
```
- Run the script and use 5 as the first argument.

#### HINTS

- Type `./countdown.sh 5` in the terminal and press enter
- Make sure you are in the `project` folder first

- I think the countdown timer is finished. Feel free to try it with some other arguments. The next one is a bingo number generator.


