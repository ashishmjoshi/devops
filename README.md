# devops




Program 1:
1.	Create file Hello.java
public class Hello {
    public static void main(String[] args) {
        System.out.println("welcome to git!");
        System.out.println("This is lab program 1");
    }
}
2.	git init
git add Hello.java 	(or git add .)
git commit -m “Initial Commit”
git log
3.	git branch b1
git switch b1
edit Hello.java:
public class Hello {
    public static void main(String[] args) {
        System.out.println("welcome to B1!");
        System.out.println("This is lab program 1");
    }
}
git add Hello.java
git commit -m “Commit using B1”
4.	git switch master (use git branch to see which branch you are in)
edit Hello.java:
public class Hello {
    public static void main(String[] args) {
        System.out.println("welcome to Master!");
        System.out.println("This is lab program 1");
    }
}
git add Hello.java
git commit -m “Commit using Master”
5.	git merge b1
(resolve merge conflict)
git add Hello.java
git commit -m “Merge Conflict Resolved”

Extra:
git version (to check git version)
git log --oneline --graph –all (for last)
git status
Remove-Item -Recurse -Force .git   (remove existing git folder – if it shows reinitialised)


Viva :
1. What is Git?
Git is a distributed version control system used to track changes in source code and manage different versions of a project.
2. What is version control?
Version control is a system that records changes made to files over time so that we can track, compare, and restore previous versions.
3. What is a repository?
A repository is a storage location where Git tracks and maintains project files and their history.
4. What is git init?
It initializes a new Git repository in the current directory.
5. What is git add?
It moves changes from the working directory to the staging area (where we select and prepare changes before committing them).
6. What is git commit?
It saves the staged changes as a snapshot in the repository's history.
7. What is git log?
It displays the commit history of the repository.
8. What is git status?
It displays the current state of the working directory and staging area.
9. What is a branch in Git?
A branch is an independent line of development that allows developers to work on different features without directly affecting the main branch. Branches allow developers to work on different features, experiment, fix bugs, and develop independently.
10. git branch: Creates or lists branches.
git switch: Changes the current branch.
11. What is merging in Git?
Merging is the process of combining changes from one branch into another branch.
12. What is a merge conflict?
A merge conflict occurs when Git cannot automatically combine changes from different branches. They commonly occur when two branches modify the same part of a file differently.
 SProgram 2:
1. Eclipse -> New -> Maven project -> next -> filter : maven-archetype-quickstart , version 1.1 -> next -> name test1
2. In source/main/java -> new class : readJSON -> checkbox: public static void main()
import java.io.File;
import com.fasterxml.jackson.databind.JsonNode;
import com.fasterxml.jackson.databind.ObjectMapper;
public class ReadJSON {
    public static void main(String[] args) {
        try {
            ObjectMapper objectMapper = new ObjectMapper();
            File jsonFile = new File("student.json");
            JsonNode studentData =
                objectMapper.readTree(jsonFile);
            System.out.println("Student Details:");
            System.out.println("----------------");
            System.out.println("Name: " +
                studentData.get("name").asText());
            System.out.println("Age: " +
                studentData.get("age").asInt());
            System.out.println("Department: " +
                studentData.get("department").asText());
            System.out.println("College: " +
                studentData.get("college").asText());
        }
        catch (Exception e) {
            e.printStackTrace();
        }
    }
}

3. In main test1 -> right click -> new -> file -> file name: student.json
{
    "name": "ABC",
    "age": 22,
    "department": "ECE",
    "college": "XYZ"
}
4. In google search maven repositories -> search Jackson databind -> choose 2nd one (Jackson databind fasterxml.jakson.core) -> choose 1st one (Jackson databind) -> scroll down to versions and click on any version without vulnerabilities -> scroll down and copy the maven code <dependencies> </dependencies>
5. open pom.xml and paste in <dependencies> </dependencies> part
Run ReadJSON file.

 Viva:
1. What is Maven?
Maven is a build automation and project management tool mainly used for Java projects.
•	Automates compilation.
•	Manages dependencies.
•	Runs unit tests.
•	Packages applications.
•	Generates deployable artifacts.
2. Who developed Maven? -> Apache Software Foundation.
3. What is a build automation tool?
A tool that automatically performs tasks such as compiling, testing and packaging source code.
4. What is dependency management?
It is the process of managing external libraries required by a project.
5. What is POM?
POM stands for Project Object Model. It contains project configuration and dependency information.
•	Group ID
•	Artifact ID
•	Version
•	Dependencies
•	Plugins
•	Build configuration
•	Packaging type
6. What is a dependency in Maven?
A dependency is an external library required by a Java project.
7. What is a Maven repository?
A repository is a location where Maven libraries and artifacts are stored.
8. What is JSON?
JSON stands for JavaScript Object Notation. It is a lightweight data-interchange format. Jackson is a Java library used to process JSON data.

9. What is ObjectMapper?
ObjectMapper is a Jackson class used to convert Java objects to JSON and JSON to Java objects.
10. What is JsonNode?
JsonNode represents JSON data as a tree structure.
11. What is readTree()?
It reads JSON content and converts it into a JsonNode tree.




 
Program 3:
using tomcat: 
1.	index.html :
<!DOCTYPE html>
<html>
<head>
    <title>Docker Experiment</title>
</head>
<body>
    <h1>Welcome to Docker!</h1>
    <p>This is Experiment 3.</p>
</body>
</html>

Dockerfile:
FROM tomcat:9.0
COPY index.html /usr/local/tomcat/webapps/ROOT/
EXPOSE 8080
CMD ["catalina.sh", "run"]

2.	docker build -t vamp:1.0 . (build docker image – vamp)
docker rm -f vcont  (removes existing container with name vcont)
docker run -d -p 8081:8080 --name vcont vamp:1.0  (run docker container)
docker ps (verify running)

3.	Test in http://localhost:8081

4.	docker login
docker tag vamp:1.0 bhoomika023/vamp:1.0
docker push bhoomika023/vamp:1.0 (push image to docker hub)
docker pull bhoomika023/vamp:1.0 (verify by pulling image)
 using latest:
1. index.html :
<!DOCTYPE html>
<html>
<head>
    <title>Docker Experiment</title>
</head>
<body>
    <h1>Welcome to Docker!</h1>
    <p>This is Experiment 3.</p>
</body>
</html>

Dockerfile:
FROM httpd:latest
COPY index.html /usr/local/apache2/htdocs/index.html
2. docker build -t vamp:latest . (build docker image – vamp)
docker rm -f vcont (removes existing container with name vcont)
docker run -d -p 8081:80 --name vcont vamp:latest (run docker container)
docker ps (verify running)
3. Test in http://localhost:8081
4. docker login
docker tag vamp:latest bhoomika023/vamp:latest
docker push bhoomika023/vamp:latest
docker pull bhoomika023/vamp:latest


 Viva:
1. What is Docker?
Docker is an open-source platform used to develop, package and run applications inside containers.
2. What is containerization?
Containerization is the process of packaging an application and its dependencies into a container so it can run consistently in different environments.
3. What is a Docker image?
A Docker image is a read-only template used to create Docker containers.
4. What is Docker Hub?
Docker Hub is a cloud-based registry where Docker images can be stored, shared, pushed and pulled.
5. What is a Dockerfile?
A Dockerfile is a text file containing instructions to build a Docker image. It automates the process of creating Docker images.
FROM: Specifies the base image.
COPY: Copies the HTML file into Tomcat's ROOT web application directory.
EXPOSE: Documents that the container listens on port 8080.
CMD: Starts the Tomcat server.
Apache Tomcat 9.0 is a web server and servlet container used to serve web applications. We use it to host our HTML page.
It copies files from the local build context into the Docker image.
It is Tomcat's default ROOT web application directory. Files placed here are served from the root URL.
It starts the Tomcat server in the foreground so that the container remains running while Tomcat is active.

 Program 4:
With github: 
Prereq: open github -> create a repo -> add a java/python file(hello.java)
1.	Open http://localhost:8080 (Jenkins, if not 8080 then 8081).
Username, Password: user
Open the Jenkins Dashboard -> New Item -> (Item name: exp9) -> Freestyle project -> OK.
In the project configuration page, go to Source Code Management -> Select github -> repo url (Note : here in branch if you get fail for main, try with master or vica versa)
Build Steps -> Add build step -> Execute Windows batch command ->
java --version
javac hello.java
-> Save.
2.	Manage Jenkins -> Plugins -> Available plugins -> Search Slack Notification -> Install.
3.	Open Slack workspace (testvvce).
Create channel -> jenkins-build-alerts.
4.	Slack -> Apps -> Browse apps -> Search Jenkins CI -> Add to Slack.
5.	Jenkins -> Manage Jenkins -> System -> Slack section -> Add -> Secret text -> Select secret from Jenkins CI -> ID: Slack-token -> Add.
Select Slack-token -> Workspace: testvvce -> Test Connection -> Success.
6.	Jenkins -> exp9 -> Configure -> Post-build Actions -> Add post-build action -> Slack Notifications -> Select all available notification options -> Save.
7.	Jenkins -> exp9 -> Build Now -> Open Slack workspace (testvvce) -> #jenkins-build-alerts -> Check for build notification.

 
Without github:
8.	Open http://localhost:8080 (Jenkins, if not 8080 then 8081).
Username, Password: user
Open the Jenkins Dashboard -> New Item -> (Item name: exp9) -> Freestyle project -> OK.
In the project configuration page, go to Source Code Management -> Select None.
Build Steps -> Add build step -> Execute Windows batch command ->
java --version
echo Jenkins Slack Integration Experiment
-> Save.
9.	Manage Jenkins -> Plugins -> Available plugins -> Search Slack Notification -> Install.
10.	Open Slack workspace (testvvce).
Create channel -> jenkins-build-alerts.
11.	Slack -> Apps -> Browse apps -> Search Jenkins CI -> Add to Slack.
12.	Jenkins -> Manage Jenkins -> System -> Slack section -> Add -> Secret text -> Select secret from Jenkins CI -> ID: Slack-token -> Add.
Select Slack-token -> Workspace: testvvce -> Test Connection -> Success.
13.	Jenkins -> exp9 -> Configure -> Post-build Actions -> Add post-build action -> Slack Notifications -> Select all available notification options -> Save.
14.	Jenkins -> exp9 -> Build Now -> Open Slack workspace (testvvce) -> #jenkins-build-alerts -> Check for build notification.

 Viva: 
1. What is Jenkins?
Jenkins is an open-source automation server used for Continuous Integration (CI) and Continuous Delivery (CD). To automate software tasks such as building, testing, and deploying applications.
A Jenkins job is a task configured to perform operations such as building, testing, or deploying a project.
2. What is CI?
Continuous Integration is the practice of frequently integrating code changes into a shared repository and automatically building and testing them.
3. What is a Freestyle project?
A Freestyle project is a basic Jenkins job that allows users to configure build steps and post-build actions through the Jenkins GUI.
4. What is the Jenkins dashboard?
It is the main interface used to create, configure, monitor, and manage Jenkins jobs.
5. What is a build in Jenkins?
A build is the execution of a configured Jenkins job.
6. What is Slack?
Slack is a cloud-based team communication and collaboration platform.



 Program 5:
1.	docker –version
kubectl version

2.	create index.html:
<!DOCTYPE html>
<html>
<head>
    <title>Netflix Movie Application</title>
</head>
<body>
    <h1>Welcome to Netflix Movie Application</h1>
    <p>Kubernetes Container Orchestration Experiment 5</p>
    <p>Application deployed successfully.</p>
</body>
</html>

create Dockerfile:
FROM httpd:latest
COPY index.html /usr/local/apache2/htdocs/index.html

3.	docker build -t kubo33 .
docker run -d --name cont3 -p 8081:80 kubo33

4.	create deployment.yml:
apiVersion: apps/v1
kind: Deployment

metadata:
  name: netflix-movie-deployment

spec:
  replicas: 3

  selector:
    matchLabels:
      app: netflix-movie

  template:
    metadata:
      labels:
        app: netflix-movie

    spec:
      containers:
      - name: movie-server
        image: netflix-movie:1.0
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080

create service.yml:
apiVersion: v1
kind: Service

metadata:
  name: netflix-movie-service

spec:
  selector:
    app: netflix-movie

  ports:
  - port: 80
    targetPort: 8080

  type: LoadBalancer

5.	kubectl apply -f deployment.yml
kubectl apply -f service.yml
verify:
kubectl get deployments
kubectl get pods
kubectl get services
6.	open http://localhost:8081
kubectl scale deployment netflix-movie-deployment --replicas=5
kubectl get pods
kubectl delete pod netflix-movie-deployment-c44b984dd-mkztl (here netflix-movie-deployment-c44b984dd-mk is the name of the pod you get in kubectl get pods)
kubectl get pods
kubectl scale deployment netflix-movie-deployment --replicas=2
7.	kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get services


 Viva:
1. What is Kubernetes?
Kubernetes is an open-source container orchestration platform used to automate the deployment, scaling and management of containerized applications.
2. What is container orchestration?
Container orchestration is the automated management of containers, including deployment, scaling, networking, load distribution and recovery.
3. What is a Pod?
A Pod is the smallest deployable unit in Kubernetes. It contains one or more containers that share network resources and can share storage.
4. What is a Node?
A Node is a machine (physical or virtual) on which Kubernetes runs Pods.
5. What is a Cluster?
A Kubernetes Cluster is a group of Nodes managed by Kubernetes.
6. What is a Deployment?
A Deployment is a Kubernetes resource that manages application Pods and maintains the desired number of replicas.
7. What is a Replica?
A replica is an instance of an application Pod.
8. What is Tomcat?
Apache Tomcat is an open-source web server and servlet container used to run Java web applications.
Docker	Kubernetes
Used to build and run containers	Used to orchestrate containers
Builds container images	Deploys and manages Pods
Runs individual containers	Manages containers across a cluster
Provides containerization	Provides orchestration
9. What is a TAR file?
A TAR file is an archive file format used to package files together. We used it to transfer our Docker image.
10. What does docker cp do?
It copies files between the host machine and a container.
11. What does docker exec do?
It executes a command inside a running container.
12. What is containerd?
Containerd is a container runtime responsible for managing container lifecycle operations, such as image management and running containers.
13. What is a YAML file?
YAML stands for YAML Ain't Markup Language. It is a human-readable data serialization format used to configure Kubernetes resources.
14. What is apiVersion?
It specifies the Kubernetes API version used for creating the resource.
15. What is kind?
It specifies the type of Kubernetes resource, such as Deployment or Service.
16. What is metadata?
It contains information about a resource, such as its name, labels and annotations.
17. What is spec?
It defines the desired configuration or state of a Kubernetes resource.
18. What does replicas: 3 mean?
It instructs the Deployment to maintain three application Pods.
19. What is a Label in Kubernetes?
A Label is a key-value pair attached to Kubernetes objects to identify and organize them.
20. What is a Selector?
A Selector is used to identify Kubernetes resources based on their labels.
