
## commandarguments

```shell
#!/bin/sh
echo "File Name: $0"
echo "First Parameter : $1"
echo "Second Parameter : $2"
echo "Quoted Values: $@"
echo "Quoted Values: $*"
echo "Total Number of Parameters : $#"	
```
$0 The filename of the current script.
$n These variables correspond to the arguments with which a script was invoked. Here n is a positive decimal number corresponding to the position of an argument (the first argument is $1, the second argument is $2, and so on).
$# The number of arguments supplied to a script.
$* All the arguments are double quoted. If a script receives two arguments, $* is equivalent to $1 $2.
$@ All the arguments are individually double quoted. If a script receives two arguments, $@ is equivalent to $1 $2.	
$? The exit status of the last command executed.	
$$ The process number of the current shell. For shell scripts, this is the process ID under which they are executing.	
$! The process number of the last background command.

## copying pub key in authorzedkeys

```shell
#!/bin/bash
# Specify the file containing the list of servers
server_list="servers.txt"
# Specify your SSH key file
ssh_key="~/.ssh/id_rsa.pub"
# Specify your username
username="root"
# Loop through each server in the list
while IFS= read -r server; do
    echo "Copying SSH key to $server..."
    cat $ssh_key | ssh $username@$server 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
done < "$server_list"

last-file-change
find . -type f -mtime -1 -print0 | xargs -0 ls -lt | head -n 1

Simple Loop
#!/bin/bash
for i in {1..5}
do
    echo $i
done

```
## Variables

```shell
#!/bin/bash  
  # Read the user input   
  echo "Enter the user name: "  
read first_name  
echo "The Current User Name is $first_name"  
echo  
echo "Enter other users'names: "  
read name1 name2 name3  
echo "$name1, $name2, $name3 are the other users."

```

## Simple Read-Line
```shell
#!/bin/bash
file="/home/jayeshkumar/jayesh.txt"
# Check if the file exists
if [ -e "$file" ]; then
while IFS= read -r line; do
echo "Line read: $line"
# Add your processing logic here
done < "$file"
else
echo "File not found: $file"
fi
```

### Function
```shell
#!/bin/sh
# Define your function here
Hello () {
   echo "Hello World"
}
# Invoke your function
Hello
```