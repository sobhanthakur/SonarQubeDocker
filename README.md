## SonarQube Server with Docker

1. Install Docker
	```
	https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository
	```
2. Once downloaded, start it to make it available in a certain port. To achieve this, execute:

	```
	docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube
	```

3. To Verify the installation, try to access http://docker-ip: port.
   ```
	eg: http://localhost:9000 or http://someIP:9000
   ```

   By default you can login as "admin" with password "admin"

4. Download the SonarQube Scanner
	
	For Linux:
    ```
    https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.2.0.1227-linux.zip
	```
	For Windows:
	```
    https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.2.0.1227-windows.zip
    ```
	For Mac:
    ```
	https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.2.0.1227-macosx.zip
    ```

5. Unzip the Source code.

6. Add the "bin" directory of the source code to the path.
   
   6.1> Append the following line to bashrc
   
      ```export PATH=$PATH:/Your-SonarQube-Scanner-Path/bin``` 
      
   6.2> Run "source ~/.bashrc" 

7. Check the basic installation by opening a new shell and executing the command ```"sonar-scanner -h"```

8. Create a configuration file in the root directory of the project, namely "sonar-project.properties".
   
   A Sample "sonar-project.properties" file:
```
   	# must be unique in a given SonarQube instance
	sonar.projectKey=my:project
	# this is the name and version displayed in the SonarQube UI. Was mandatory prior to SonarQube 6.1.
	sonar.projectName=My project
	sonar.projectVersion=1.0
	 
	# Path is relative to the sonar-project.properties file. Replace "\" by "/" on Windows.
	# This property is optional if sonar.modules is set. 
	sonar.sources=.
	 
	# Encoding of the source code. Default is default system encoding
	#sonar.sourceEncoding=UTF-8

	#Exclude following directories from being analyzed.
	sonar.exclusions=vendor/**, var/**
   ```

9. Run ```sonar-scanner``` from the root directory of your project.
   It will start analyzing the project.

10. After Successful execution, go to the browser and access the page, http://localhost:9000
	You would find your project listed under “PROJECTS”. Click on your project listing and you would land up on the project dashboard.
