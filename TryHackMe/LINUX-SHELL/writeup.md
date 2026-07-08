writeup..md
=  COMMANDS =

- echo SHELL - command that gives you the current shell you are using (LINUX).
- cat /etc/SHELL - show the list of shells that are currently installed in LINUX system.
- chsh -s - to permanently changed your current shell,, 
        ex. chsh -s /usr/bin/zsh
- history - to view your latest used commands



TAKEAWAYS: 
1. Shell scripting and Components:
-- to make a script we need 1st to make a file, to make a file we can use the command " nano 'filename.sh' "
-- every script should start from shebang. Shebang is a combination of some characters that are added at the beginning of a script, starting with '" #! " followed by the name of the interpreter to use while executing the script. As we are writing our script in bash, let’s define it as the interpreter in the shebang.
-- so output should be (inside the file) = #!//bin/bash
-- after successfully making a file with contents, to save it we use " CTRL+X " then Y for yes and then Enter.
-- next,, for executing a script we 1st need to enable the executing permission for it, so we use the command " chmod +x 'filename.sh' "
-- lastly,, we use command " ./ " to make execution permission for the given file.
    ex. ./filname.sh 


ex. Script; Variables*
1. Variables = variables store value inside it.
ex.  
#!/bin/bash
echo "Hey, what’s your name?"
read name
echo "Welcome, $name"

2. Loops = something that is repeating. 
ex.
#!/bin/bash
for i in {1..10};
do
echo $idone

3. Conditional Statemens = it help you execute a specific code only when a condition is satisfied; otherwise, you can execute another code. 
ex.
#!/bin/bash
echo "Please enter your name first:"
read name
if [ "$name" = "Stewart" ]; then
echo "Welcome Stewart! Here is the secret: THM_Script"
else
echo "Sorry! You are not authorized to access the secret."
fi

4. Comments = A comment is a sentence that we write in our code just for the sake of our understanding. 
ex. 
#!/bin/bash
# Asking the user to enter a value.
echo "Please enter your name first:"

# Storing the user input value in a variable.
read name

# Checking if the name the user entered is equal to our required name.
if [ "$name" = "Stewart" ]; 

then

# If it equals the required name, the following line will be displayed.
echo "Welcome Stewart! Here is the secret: THM_Script"

# Defining the sentence to be displayed if the condition fails.
else

echo "Sorry! You are not authorized to access the secret."
fi

