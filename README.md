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
3. 
   
