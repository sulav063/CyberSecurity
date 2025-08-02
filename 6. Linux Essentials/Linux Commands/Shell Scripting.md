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
You can create and edit these scripts using:

```bash
mousepad script_name &
```

- This opens the script in a GUI text editor (`mousepad`) in the background so your terminal stays free.
Use `Ctrl + C` to exit a running command or cancel an operation in terminal.
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
echo "Modulus of $num1 and $num2 is $modulo"

# Comparison Operators
if [ "$num1" -eq "$num2" ]; then
    echo "Both numbers are equal"
else
    echo "Numbers are not equal"
fi
```

---
## Script 6 - Greater, Equal, or Smaller
```bash
#!/bin/bash

read -p "Enter a number: " num

# Check if the number is greater than, equal to, or less than 10
if [ "$num" -gt 10 ]; then
    echo "The number is greater than 10"
elif [ "$num" -eq 10 ]; then
    echo "It is exactly 10"
else
    echo "It is less than 10"
fi
```

---
## Script 7 - Odd or Even
```bash
#!/bin/bash

read -p "Enter a number: " num

# Check if the number is even or odd
if (( num % 2 == 0 )); then
    echo "The number is even"
else
    echo "The number is odd"
fi
```

---
## Script 8 - Simple Calculator (Using if-else)
```bash
#!/bin/bash

echo "Simple Bash Calculator using if-else"
echo "------------------------------------"

read -p "Enter first number: " num1
read -p "Enter second number: " num2

echo "Choose operation: +  -  *  /"
read -p "Enter operator: " op

if [ "$op" = "+" ]; then
    result=$((num1 + num2))
    echo "Result: $num1 + $num2 = $result"

elif [ "$op" = "-" ]; then
    result=$((num1 - num2))
    echo "Result: $num1 - $num2 = $result"

elif [ "$op" = "*" ]; then
    result=$((num1 * num2))
    echo "Result: $num1 * $num2 = $result"

elif [ "$op" = "/" ]; then
    if [ "$num2" -ne 0 ]; then
        # Using bc for floating point division with 2 decimal places
        result=$(echo "scale=2; $num1 / $num2" | bc)
        echo "Result: $num1 / $num2 = $result"
    else
        echo "Error: Cannot divide by zero"
    fi

else
    echo "Invalid operator. Please use +, -, * or /"
fi

```
---
## Script 9 - System Commands in Shell Scripting
System commands are built-in or external utilities provided by the Linux/Unix operating system. These commands allow you to manage system-level tasks like checking the user, hostname, OS, and network configuration.

### Basic System Info Script
```bash
touch sys_cmd
chmod +x sys_cmd
mousepad sys_cmd&
```

```bash
#!/bin/bash
# System Commands

touch ./data.txt

uname=$(whoami)
sysname=$(hostname)
netinfo=$(ifconfig)
osinfo=$(uname -a)

echo "Username: $uname" >> data.txt
echo "Username is collected..."

echo "Hostname: $sysname" >> data.txt
echo "Hostname is collected..."

echo "Network info: $netinfo" >> data.txt
echo "Network information is collected..."

echo "OS info: $osinfo" >> data.txt
echo "OS information is collected..."
```

### Commands Used

| Command    | Purpose                                    |
| ---------- | ------------------------------------------ |
| `whoami`   | Displays current logged-in user            |
| `hostname` | Shows system hostname                      |
| `ifconfig` | Displays network configurations            |
| `uname -a` | Prints kernel name and full OS information |
| `touch`    | Creates a new empty file                   |
| `echo`     | Prints text or variable to terminal/file   |
### Output of './sys_cmd '

```txt
Username is collected...
Hostname is collected...
Network information is collected...
OS information is collected...
```
### Output of `data.txt`

```txt
Username: student
Hostname: ubuntu-machine
Network info: eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          ...
OS info: Linux ubuntu-machine 5.15.0-100-generic #1 SMP Mon May 6 ...
```

---

## Script 10 - Alive System Check Script

```bash
#!/bin/bash
# Alive system check

read -p "Enter an IP to check: " ip

ping -c 4 $ip | grep "64 bytes" > test.txt

if [ -s test.txt ]; then
  echo "System is alive"
else
  echo "System is not alive"
fi
```

### Explanation

|Line|Function|
|---|---|
|`read`|Gets user input (IP address)|
|`ping`|Sends ICMP packets to the given IP|
|`grep`|Filters response lines containing "64 bytes"|
|`-s`|Checks if `test.txt` is non-empty|
|`if-else`|Prints if the system is alive or not|
### Output of './sys_cmd '
```bash
chmod +x sys_cmd.sh   # Make script executable
./sys_cmd             # Run the script
```

```txt
OS information is collected...
Enter an IP to check: 1.1.1.1
System is alive
```
### Possible Output of `test.txt`
```bash
cat test.txt
```

```txt
64 bytes from 192.168.1.10: icmp_seq=1 ttl=64 time=0.052 ms
64 bytes from 192.168.1.10: icmp_seq=2 ttl=64 time=0.048 ms
64 bytes from 192.168.1.10: icmp_seq=3 ttl=64 time=0.050 ms
64 bytes from 192.168.1.10: icmp_seq=4 ttl=64 time=0.049 ms
```

---

## Script 11 - File exits or not
```bash
touch file_check.sh
chmod -x file_check.sh
mousepad file_check.sh&
```

### file_check.sh 'script'
```bash
#!/bin/bash

# Ask user for a file name
echo -n "Enter the file name: "
read FILENAME

# Check if file exists
if [ -e "$FILENAME" ]; then
    echo "$FILENAME already exists."
else
    echo "Creating $FILENAME..."
    echo "This is a new file." > "$FILENAME"
    echo "$FILENAME has been created."
fi
```

```bash
./file_check.sh       #Run Script
```

### Possible Output
```txt
Enter the file name: notes.txt
Creating notes.txt...
notes.txt has been created.
				OR
Enter the file name: notes.txt
notes.txt already exists.
```

---
## Script 12 - Ping Swift

### What is `ping`?
The `ping` command is a **network utility** used to **test connectivity** between two devices (hosts) on a network. It works by sending **ICMP (Internet Control Message Protocol)** **Echo Request** packets to a target host and waiting for an **Echo Reply**.
- If the target responds, it is considered **reachable**.
- If there is no reply, the host might be **offline**, **unreachable**, or **not responding to ICMP**.
### What is `swift` in `ping swift`?
In the command `ping swift`, the word **`swift`** is a **hostname** — a **human-readable name** assigned to a device on the network.
- Hostnames are used instead of IP addresses to make communication easier.
- Before the `ping` command can work, the system must **resolve the hostname `swift` to an IP address**.
- This is done using:
    - The **`/etc/hosts`** file (local hostname mappings)
    - Or a **DNS (Domain Name System)** server (for network-wide resolution)
### pingswift.sh 'script'
```bash
#!/bin/bash

if [ "$1" == "" ]; then
    echo "You forgot to enter an IP base!"
    echo "Usage: ./pingsw3p.sh 192.168.1"
else
    echo "Scanning network: $1.0/24 ..."

    for ip in $(seq 1 254); do
        full_ip="$1.$ip"
        ping -c 1 -W 1 $full_ip > /dev/null

        if [ $? -eq 0 ]; then
            echo "$full_ip is up"
            break  # stop scanning after finding first up host
        fi
    done
fi
```