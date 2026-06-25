# DSCC — 25-06-26

Creating and pushing in a docker files.

Step1: Open Docker hub software.

Step2: Also login in to your Dockerhub id via browser.

1) Create a new folder:

i created DSCC.

Inside the folder save a text file named "Dockerfile". (File should not have extensions).

2) type "FROM ubuntu"

save the file.

3) change directory this folder (DCSS in my case)

```
cd DSCC
```

4) Execute the below command. (Dockerfile is the filename)

```
docker build . < Dockerfile
```

5) type the command below:

```
docker image
```

You shall be getting something like this:

![docker image output](images/step5.png)

6) I created another folder named "Folder 2" inside "DSCC" folder. You can name 2 seperate folders (it's your wish).

7) Open notepad and again create a file named "Dockerfile" in the new folder (Folder2):

- save the file and now change directory to "Folder2" (as given in image).

![folder2 directory](images/step7.png)

- also type the subsequent command as given in image.

![step7 command](images/step7b.png)

8) Now you have 2 images stored in "Images" in docker. The icon is below:

![docker images icon](images/step8.png)

9) Run the image created and stored in Docker hub:

![run image](images/step9.png)

10) Observe "Status" here, you will be getting something like "exited in 1 seconds".

11) Create new repo 'firstdockerimage' in repo at dockerhub.com

12) Ensure the Repository is "Public".

13) Username/firstdockerimage is your repository name here.

14) Run the command :

```
docker tag demoimage Username/firstdockerimage
```

Here you can see the details of two images. (One from DCSS folder and another one from Folder2)

15) Now push both the images with the below command:

```
docker image push -a  Username/firstdockerimage
```

16) Images are now pushed in docker hub repo. View the images in repo:

![pushed images](images/step16.png)

---

(Ignore)

1. base image: FROM busybox
2. Install the necessary library
