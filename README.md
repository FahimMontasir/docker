# file: Dockerfile

FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js

.....................................................
to download ubuntu in my pc
docker run ubuntu
docker ps // to see running list of processes use -a to see all container
docker run -it ubuntu //to run ubutu in iteractive mode
echo hello //to print hello
whoami
echo $0 //to know where its downloaded
history //to see all command i typed
!2 // execute second command
//linux is case censetive
...........................................................

apt //like npm or yarn
apt list //to see all packages
apt update
apt install <package name> // apt install nano
nano // to open nano text editor
apt remove nano // to remove nano
............................................................

pwd //to see root directory
ls //list of files -1 -l
cd bin //navigate to other file /absolute
cd .. // back
cd ~ // to go home directory
cd . //current dir
.............................................................
cd ~
mkdir test //make dir
ls
mv test docker //move or rename file and folder
touch hello.txt //to create a new file
rm file.txt //remove file file\*(stating with file)
rm -r docker/ //to remove directory recursively
.................................................................

nano file.txt // to open file in nano editor
cat file.txt //to see content of a file
more file.txt //to see long doc page by page press space bar to go next page and press q to quit the file
less /etc/adduser.config // to see all content use up and down arrow to navigae line
.....................................................................
------redirection operation (>)
cat file1.txt file2.txt //concat two file and print
cat file.txt > file1.txt // move file.txt content to file1.txt and display
cat file1.txt file2.txt > cobine.txt
echo whater > file1.txt
ls -l /etc > files.txt // to show the log listing of etc dir
.....................................................................
seach text
grep -i hello file1.txt
...................................................................
finding files and directories:
ls -a //to see hidden file
find -type d //find directory
find / -type f -name "\*.py" > py-files.txt//find all files in root directory name end with .py and redirect to py-files.txt
cat py-files.txt
.....................................................................
chaining commands:
mkdir test ; cd test ; echo done
mkdir test && cd test // if first c. executes then second c.
mkdir test || cd test
ls /bin | less
\ //to add new line
................................................................
environment variable:
printenv
printenv PATH //to see path variable
export DB_USER=fahim //only availabe on the current session
docker ps -a
docker start -i id //id of ubuntu container
ls -a
echo DB_USER=fahim >> .bashrc //to store env permenently
sourse ~/.bashrc //to reload
...........................................................
managin prosses:
ps
sleep 3 //sleep 3sc
sleep 100 & //backgroud sleep
kill 38(prossed id)
.................................................................
managin users:
useradd usermod userdel
useradd -m fahim
cat /etc/passwd
usermod -s /bin/bash fahim
cat /etc/passwd
cat /etc/shadow
docker exe -it -u fahim id bash
..............................................................
managing groups:
groupadd groupmod groupdel
groupadd -m developers
usermod -G developers fahim
....................................................................
file permission:
echo echo hello > deploy.sh //.sh will execute echo hello to the terminal
ls -l // to see permission
chmod u+x deploy.sh

<<<<<<<<<< building Images >>>>>>>

dokerfile:
FROM
WORKDIR
COPY
ADD
RUN
ENV
EXPOSE
USER
CMD
ENTRYPOINT
...............................................................

FROM node:16.9.1-alpine3.14

docker build -t react-app . //tag react-app and build in current dir
docker images //to see all images
docker run -it react-app
docker run -it react-app sh // run with shall
....................................................................
WORKDIR /app
COPY .(source) .(docker) //copy everything from the current dir to /app
docker build -t react-app .
...............................................................
.dockerignore //add everything that dont need e.g node_modules
................................................................
running commands
RUN npm install //run any command
..................................................................
setting env variables:
ENV API_URL=http://api.anyurlweneed.com/
docker built -t react-app .
docker run -it react-app sh
printenv
printenv API_URL
.....................................................................
exposing port:
EXPOSE 300
..................................................................
setting a user for squrity reson:
docker run -it alpine
adduser
addgroup app
adduser -S -G app(group name) app(user name)
groups app
addgroup fahim && adduser -S -G fahim fahim
groups fahim

RUN addgroup app && adduser -S -G app app
USER app
docker build -t react-app .
docker run -it react-app sh
whoami
ls -l
...............................................................
defining entrypoints:

docker run react-app npm start //dont use iteractive mode

FROM node:14.16.0-alpine3.13
RUN addgroup app && adduser -S -G app app
USER app
WORKDIR /app
copy . .
RUN npm install
ENV API_URL=http://api.myapp.com/
EXPOSE 300
CMD ["npm", "start"] //runtime instrution cmd=entrypoint(has additioinal fet)

docker built -t react-app .
docker run react-app
.................................................................
speed up builds:
dcoker history react-app

WORKDIR /app
COPY packag\*.json .
RUN npm install
COPY . .
..................................................................
removing images:
docker images
docker image prune
docker ps
docker ps -a
docker container prune
docker image prune
docker images
docker image
docker images
docker image rm ubuntu // ubuntu will be removed
..................................................................
Taging images:
docker build -t react-app . //fresh build
docker build -t react-app:1 . // tag is 1
docker image remove react-app:1
docker image tag react-app:latest react-app:1 //new tag added later
change something then
docker build -t react-app:2 .
docker images
docker image tag b06(id) react-app:latest
docker images
...................................................................
sharing images:
docker image tag bo6(id) codewithmosh/react-app:2
docker images
docker login
docker push codewihtmosh/react-app:2
chane something
docker build react-app:3 .
docker images
docker image tag react-app:3 codewithmosh/react-app:3
docker push codewihtmosh/react-app:3
now we can pull images
...................................................................
saving and loading image:
image save --help
docker image save -0 react-app.tar react-app:3 //save iamge as .tar file
docker load --help
docker image rm react-app:3
docker images
docker image load -i react-app.tar //to load image
....................................................................

<<<<<<<<working with containers>>>>>>>

starting containers:
docker images
docker ps
docker run -d react-app //run in the bg
docker ps
docker run -d --name blue-sky react-app //naming the container(blue-sky)
