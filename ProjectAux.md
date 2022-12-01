# Documentation for Project: AUX PROJECT 1: SHELL SCRIPTING

## Preparing prerequisites

- Create a new EC2 Instance of t2.nano family with Linux Server 20.04 LTS (HVM) image.

[Onboard Script](https://github.com/darey-devops/Auxilarry-project-1/blob/main/onboard.sh)

- Create an onboard folder on the local machine (in the folder where the pem key is stored):

`vi onboard.sh`

- Copy the Onboard shell file to the Ubuntu serverby running the command below

`scp -i segun-ec2.pem Onboard.sh ubuntu@3.17.29.169:~/;`

![Copy Onboard to Ubuntu1](./imagesAux/copy-onboard-to-ubuntu.PNG)

- To confirm Onboard.sh is on the server:

`ls -l`

![To Show Onboard.sh is on the server](./imagesAux/To-confirm-Onboard.sh-in-server.PNG)

Create the project folder called Shell:

`mkdir Shell`

- Move into the Shell folder

`cd Shell`

- ![Create Shell folder & Cd to Shell](./imagesAux/create-shell-folder-cd-to-shell.PNG)

- Move the onboard.sh file into the Shell folder:

- Cd back to home and run the command below:

`mv onboard.sh /home/ubuntu/Shell/`

![Create to Home](./imagesAux/mv-onboard-shell-folder.PNG)

- Cd back to the Shell folder:

`cd Shell/`

- To confirm the onboard.sh file is in the Shell folder:

`ls`

![Confirm Onboard is in Shell](./imagesAux/confirm-onboard-is-in-shell.PNG)

- Create required files:

`touch id_rsa id_rsa.pub names.csv`

- To popluate the created files:

- To copy the public key:

`vi id_rsa.pub`

- ![Write to the Id_rsa.pub](./imagesAux/write-idsapub-output.PNG)

- To copy the private key:

`vi id_rsa`

![Write to the Id_rsa](./imagesAux/write-idsa-output.PNG)

To edit names.csv:

`vi names.csv`

![Names Ouput](./imagesAux/names-csv-output.PNG)

`pwd`

- ![Pwd Ouput](./imagesAux/pwd-output.PNG)

- To update the Onboard file with the Shell home:

`vi onboard.sh`

![Shell Onboard Ouput](./imagesAux/shell-onboard-update-output.PNG)

- Create a group in the server:

`sudo groupadd developers`

- To make the onboard.sh file executable:

`sudo chmod +x Onboard.sh`

- Run this command to display Admin rights:

`./onboard.sh`

![Onboard Ouput](./imagesAux/admin-to-onboard.PNG)

- To Switch to a Superuser:

`sudo su`

![Switch to Superuser](./imagesAux/switch-to-superuser.PNG)

- Run the command below as a super user:

`./onboard.sh`

![Superuser Run line 109](./imagesAux/superuser-command.PNG)

To confirm the status of the onboard file:

`ls -l /home/`

![Onboard Home Output](./imagesAux/onboard-confirm-output.PNG)

- Confirm Developers group id:

`getent group developers`

![Developers group id](./imagesAux/developers-group-output.PNG)

- Confirming individual developers id:

`cat /etc/passwd`

![Individual Developers assigned Id](./imagesAux/developers-assign-id.PNG)

- To filter the users, run the command below:

`cat /etc/passwd | awk -F':' '{ print $1}' | xargs -n1 groups`

![Filter User Output](./imagesAux/filter-output.PNG)

- Test a few of the users randomly, and ensure that you are able to connect to the server using the private key and the public key:

- Copy the private key from the document into a .pem file and save it inside your download folder.

- Open another power shell terminal and run this commmand to onboard a developer:

`ssh -i oluse.pem developers@public-ip` (`ssh -i oluse.pem Alfred@3.15.199.227`)

![Connecting to the server](./imagesAux/output-connection.PNG)

- Checking the priviledges of the user:

`ls -la`

![Ls la Output](./imagesAux/ls-la-output.PNG)

`ls -la .ssh/`

![Ls la ssh Output](./imagesAux/ls-la-ssh-folder-output.PNG)

- To exit the previous user

`exit`

- Onboard a second user:

`ssh -i oluse.pem developers@public-ip` (`ssh -i oluse.pem Beckham@3.15.199.227`)

![User 2](./imagesAux/onboard-second-user.PNG)

- To confirm the user does not have admin access:

`sudo apt update`

![No Admin access](./imagesAux/to-confirm-user-donot-av-admin-rights.PNG)

- To confirm ssh file was created for the second user

`ls -la .ssh/`

![To confirm .ssh file was created](./imagesAux/confirm-ssh-file-created.PNG)

Run the cat command to display the public key:

`cat .ssh/authorized_keys`

![Public Key Display](./imagesAux/public-key-display.PNG)

- To exit the user:

`exit`

N.B.

- I encountered the error attached in the screenshot below when I first ran this command:

`./onboard.sh`

![Error output](./imagesAux/error-encountered.PNG)

Solution:

- Install "dos2unix" using the link below

[Helpful links](https://askubuntu.com/questions/1117623/how-to-install-dos2unix-on-a-ubuntu-app-on-a-windows-10-machine)

- Run the onboard.sh with this command in the shell folder in the terminal:

`dos2unix onboard.sh`

[Helpful links](https://www.geeksforgeeks.org/dos2unix-unix2dos-commands/?tab=article)

- Then re-run this command

`./onboard.sh`

![Fix Output](./imagesAux/fix-outcome.PNG)