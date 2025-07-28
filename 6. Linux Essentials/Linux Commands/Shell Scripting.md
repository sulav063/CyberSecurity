
## Shebang: `#!/bin/bash`

```bash
#!/bin/bash
```

- This line tells the system to execute the script using the Bash shell.
    
- It's required at the top of every Bash script to define the interpreter.
    

---

## Making Scripts Executable

```bash
chmod +x script_name
```

- Adds execute (`+x`) permission to the script.
    
- This allows the user to run the script directly using `./script_name`.
    

```bash
./script_name
```

- Executes the script in the current directory.
---

## Script 1 – Basic Echo and Variables

```bash
#!/bin/bash

echo "Hello world" # Print text

name=sulav
echo "Hello, $name" # Variable usage

age=23
echo "Congrats! on you $age birthday"

home_town=kathmandu
echo "I am from $home_town"

echo "Your path is $PATH" # Display system PATH
echo "Your shell is $SHELL" # Display shell
```

---

## Script 2 – Arithmetic Operations

```bash
#!/bin/bash

# Arithmetic Operations
num1=20
num2=10

sum=$((num1 + num2))
echo "the sum is $sum"

diff=$((num1 - num2))
echo "the difference is $diff"
```

---

## Script 3 – User Input

```bash
#!/bin/bash

# Getting user input
echo "please enter your name:"
read name

echo "Greeting to $name"

read -p "Enter your age: " age
echo "Cheers to your $age"
```

---

##  Script 4 – Calculation with User Input

```bash
#!/bin/bash

# Calculation test
echo "Welcome to calculations"
read -p "Enter 1st num: " num1
read -p "Enter 2nd num: " num2

sum=$((num1 + num2))
diff=$((num1 - num2))
mul=$((num1 * num2))
div=$((num1 / num2))

echo "sum is $sum, difference is $diff, multiplication is $mul, divison is $div"
```

---

## Script 5 – Operators and Conditionals

```bash
#!/bin/bash

# Supported Operators
num1=9
num2=5

modulo=$((num1 % num2))
echo "Modulus of \$num1 and \$num2 is \$modulo"

# Comparison Operators
if [ "$num1" -eq "$num2" ]; then
    echo "Both numbers are equal"
else
    echo "Numbers are not equal"
fi
```

---

You can create and edit these scripts using:

```bash
mousepad script_name &
```

- This opens the script in a GUI text editor (`mousepad`) in the background so your terminal stays free.
Use `Ctrl + C` to exit a running command or cancel an operation in terminal.
---
