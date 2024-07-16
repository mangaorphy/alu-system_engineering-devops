Script Explanation
Here's a breakdown of the script:

The shebang line #!/bin/bash tells the system to use the Bash shell to execute the script.
The comment # Accepts 4 parameters explains the purpose of the script.
The if statement checks if the number of passed parameters ("$#") is not equal to 4. If that's the case, it prints the usage information and exits the script with a non-zero status code (1), indicating an error.
The variables PATH_TO_FILE, IP, USERNAME, and PATH_TO_SSH_KEY are assigned the values of the corresponding passed parameters.
The scp command is used to transfer the file from the client to the server. The options used are:
-o StrictHostKeyChecking=no: This disables strict host key checking, which is required by the prompt. This ensures that the script can connect to the server without any interactive prompts.
-i "$PATH_TO_SSH_KEY": This specifies the path to the SSH private key that scp should use for authentication.
"$PATH_TO_FILE": This is the path to the file to be transferred on the client side.
"$USERNAME@$IP:~/": This is the destination path on the server. The file will be copied to the user's home directory (~).
