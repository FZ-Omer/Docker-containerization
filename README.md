# Docker-containerization
This repository is all about documentation of basic installation and containerization of a basic project without docker composing.

STEP 1: 
        Create a Docker account and Install docker desktop to your local machine (If not previously installed)

STEP 2:
        Create a DockerFile in the same root directory of the project.

STEP 3: 
        For our project, We've created a basic flask Hello world. And this doesnt have any database or any higher dependencies implemented.
        The dockerfile should be named 'Dockerfile'. No file format or extensions is required.

STEP 4:
        Next create a requirements.txt file containing the dependencies along with their version required for our project.

STEP 5:
        Go to the terminal and run the following commands:
          
 
        docker login 
        
(to authenticate our account, it will prompt for username and password , fill it)
          Once it displays login succeeded
           
        docker build -t enter_image_name:v.0.0.0 .     
          
    
( here you should enter the resource name and version of the project and IMPORTANTLY!!!  i added dot in the end which represents            {url} of the dockerfile directory )

STEP 6:
        Tagging our image
        
        docker tag build_image_name username/build_image_name

( The reason why we are tagging our image is because if we didnt do this step we wouldn't be able to push the image to the 
        dockerhub, you will probably get an error states that access denied.) 

STEP 7:
        Pushing the image to dockerhub
        
        docker push username/build_image_name
        
(Now if we logged into our dockerhub we can see our image has been uploaded)


----------   ON PRODUCTION SERVER   ------------ 

Here for our project in our company we used vps ubuntu hosting as our server 

STEP 1:
        Docker installation on our server. Kindly go through the below documentations for step by step process
    https://docs.docker.com/engine/install/ubuntu/ --- follow the first method which is Install using the apt repository

STEP 2:
       Pull the image to our server docker engine from docker hub using:
        
        docker pull username/build_image_name

STEP 3:
        Since we are using nginx here we have to set up a .config file in etc/nginx/sites-available/filename.config
        

(Check our repo for how to structure the config file )

STEP 4:
        Now we have to link the config file from the sites avaialable folder to the sites enabled folder.

        sudo ln -s /etc/nginx/sites-available/dockertest /etc/nginx/sites-enabled/

STEP 5:
        Now restart the nginx server for the changes to take place.

        sudo systemctl restart nginx

STEP 6:
        Now run the docker image so that the container starts running

        docker run -d -p 8080:5000 username/image_build_name:v

Now the website should be up and running. It should show up in the provided domain name.

        
