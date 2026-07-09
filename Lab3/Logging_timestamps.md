DSCC Lab3 Task 2                                                                                                    09-07-2026

Capturing time stamps in a log.txt file.

-These logs are initially stored in the volumes section in the dockerhub desktop.

-Below commands logs the time stamp in a text file and stores it in volumes section: 

```
docker run -d --name ts-logger -v $(pwd)/data:/data loggendockerimage
```
Folder Strucutre:

<img width="1142" height="691" alt="image" src="https://github.com/user-attachments/assets/d8b0f167-c261-4992-98d6-817a81fb7db2" />


<img width="1920" height="326" alt="image" src="https://github.com/user-attachments/assets/d2f1a908-5194-4fe9-9f81-273e2ba7c4a1" />

captured login time stamps extracted from volumes section in docker-engine:

<img width="1121" height="1058" alt="image" src="https://github.com/user-attachments/assets/a96bb0e6-c633-4951-8e3f-067be1767eb7" />


<img width="1917" height="457" alt="image" src="https://github.com/user-attachments/assets/f12f5d95-b2f2-4dab-b619-7a625312c31c" />

<img width="1920" height="213" alt="image" src="https://github.com/user-attachments/assets/a068df53-5fc2-44a8-9bf4-897c1946b030" />

<img width="663" height="651" alt="image" src="https://github.com/user-attachments/assets/e503110c-451e-400b-b1fd-e8b0c1376c36" />

<img width="1017" height="348" alt="image" src="https://github.com/user-attachments/assets/5cccbf6f-eae0-40ec-b75a-b0e85b305149" />

Pushed Image:

<img width="1920" height="931" alt="image" src="https://github.com/user-attachments/assets/2422e19b-1f20-4eb5-9ba1-1fd2ed2f9536" />

