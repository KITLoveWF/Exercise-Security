# Exercise-Security

### Prepare for the lab environment:
The Dockerfile is used to build docker image with full required packages for Hands-On Assembly & Security labs. <br>
**How to use:**<br>
1. Install docker on your computer (host machine) <br>
2. Build the image "img4lab" that comprises all required packages for labs <br>
`$> docker build -t img4lab .` to build docker image <br>
3. Run docker container from previously built image <br> 
`$> docker run -it --privileged -v $HOME/Seclabs:/home/seed/seclabs img4lab` <br>
`Seclabs` is created inside student's home folder
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
`$> disas secretFunc`
<img align="center" width="100" height="100" src="https://raw.githubusercontent.com/KITLoveWF/Exercise-Security/main/secretFuncAddress.png" />

   
