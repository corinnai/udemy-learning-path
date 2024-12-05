- [DevOps Project - Java Spring Boot app](#devops-project---java-spring-boot-app)
- [Stage 1: Create a Private GitHub Repository](#stage-1-create-a-private-github-repository)
  - [Step 1: Create the Repository](#step-1-create-the-repository)
  - [Step 2: Add the Project Files](#step-2-add-the-project-files)
  - [Step 3: Verify](#step-3-verify)
- [Stage 2: Deploy the App Locally](#stage-2-deploy-the-app-locally)
  - [1.   Install Java JDK](#1---install-java-jdk)
    - [Step 1: Download JDK](#step-1-download-jdk)
    - [Step 2: Install JDK](#step-2-install-jdk)
    - [Step 3: Set Environment Variables for Java](#step-3-set-environment-variables-for-java)
    - [Step 4: Verify Installation](#step-4-verify-installation)
  - [2. Install Maven](#2-install-maven)
    - [Step 1: Download Maven](#step-1-download-maven)
    - [Step 2: Install Maven](#step-2-install-maven)
    - [Step 3: Set Environment Variables for Maven](#step-3-set-environment-variables-for-maven)
    - [Step 4: Verify Installation](#step-4-verify-installation-1)
  - [3. Install MySQL](#3-install-mysql)
    - [Step 1. Download MySQL](#step-1-download-mysql)
    - [Step 2.  Install MySQL](#step-2--install-mysql)
    - [Step 3. Add MySQL to PATH Environment Variable](#step-3-add-mysql-to-path-environment-variable)
    - [Step 5. Start MySQL Server](#step-5-start-mysql-server)
- [Stage 3 : Deploy the app and database on AWS or Azure using Virtual Machines. Automate it via Bash provision scripts that work in user data.](#stage-3--deploy-the-app-and-database-on-aws-or-azure-using-virtual-machines-automate-it-via-bash-provision-scripts-that-work-in-user-data)
  - [DB instance](#db-instance)
    - [Step 1 : Launch instance](#step-1--launch-instance)
    - [Step 2:](#step-2)
  - [APP instance](#app-instance)
    - [Step 1 : Launch instance](#step-1--launch-instance-1)
    - [Step 2:](#step-2-1)
- [Stage 4  Deploy the app and database on AWS or Azure using containers running on a Virtual Machine (Docker Compose). Automate it via Bash provision scripts that work in user data.](#stage-4--deploy-the-app-and-database-on-aws-or-azure-using-containers-running-on-a-virtual-machine-docker-compose-automate-it-via-bash-provision-scripts-that-work-in-user-data)
  - [Step 1: Prepare the Environment](#step-1-prepare-the-environment)
  - [Step 2: Build the JAR File Locally](#step-2-build-the-jar-file-locally)
    - [Step 1: Install Maven](#step-1-install-maven)
    - [Step 2: Install JDK](#step-2-install-jdk-1)
    - [Step 3 : Install MySQL(dont need - used docker compose)](#step-3--install-mysqldont-need---used-docker-compose)
    - [Step 4: Building with Maven](#step-4-building-with-maven)
  - [Dockerfile](#dockerfile)
    - [Step 1 :](#step-1-)
    - [Step 2: Build the Docker Image](#step-2-build-the-docker-image)
  - [Database SQL Seeding](#database-sql-seeding)
  - [Create the `docker-compose.yml` file](#create-the-docker-composeyml-file)
  - [Launching an EC2 instance](#launching-an-ec2-instance)
    - [Step 1: Prepare the Virtual Machine](#step-1-prepare-the-virtual-machine)
    - [Step 2: Prepare Docker-Related Files](#step-2-prepare-docker-related-files)
  - [Create a Provisioning Script](#create-a-provisioning-script)



# DevOps Project - Java Spring Boot app
----
# Stage 1: Create a Private GitHub Repository
## Step 1: Create the Repository
1. Log in to **GitHub**.
2. Click the green **New button** in the repository section.
3. Name the repository `library-java17-mysql-app`.
4. Set it to **Private**.
5. Add a **README.md file**
6. Click **Create Repository**.


##  Step 2: Add the Project Files

1. Clone the repository locally
    ```bash
    git clone <your-repo-url>
    ```

2. Copy the extracted `library-java17-mysql-app` folder into the cloned repository.
3. Navigate to the project directory
    ```bash
    cd library-java17-mysql-app
    ```
4. Initialize Git, add all files, and commit:
    ```
    git add .
    git commit -m "Initial commit: Library project files"
    git push origin main
    ```
## Step 3: Verify
- Go to your repository on GitHub and confirm all the project files (including the SQL file and README) are present.
-----

# Stage 2: Deploy the App Locally

## 1.   Install Java JDK
### Step 1: Download JDK
1. Visit the Java Downloads page : https://www.java.com/en/download/
2. Download the latest version of JDK for Windows (e.g., JDK 17 or later).
### Step 2: Install JDK
1. Run the downloaded .exe file.
2. Follow the installation wizard:
    - Accept the license agreement.
    - Choose an installation path (default is C:\Program Files\Java\jdk-<version>).
### Step 3: Set Environment Variables for Java
1. Open **System Properties**:
    - Press `Win + S` → Search for **Environment Variables** → Click **Edit the system environment variables**.
2. In the **System Properties** window, click **Environment Variables.**
3. Add a new **System Variable**:
    - **Variable Name**: `JAVA_HOME`
    - **Variable Value**: `C:\Program Files\Java\jdk-<version> (or your JDK installation path).`
4. Update the `Path` variable:
    - Find **Path** under **System Variables** and click **Edit**.
    - Add: `%JAVA_HOME%\bin`.
### Step 4: Verify Installation
```
java -version
javac -version
```

## 2. Install Maven

### Step 1: Download Maven
1. Visit the Maven Downloads page https://maven.apache.org/download.cgi
2. Download the Binary zip archive for Windows.

### Step 2: Install Maven
1. Extract the downloaded `.zip` file to a directory `(e.g., C:\Program Files\Maven)`.

### Step 3: Set Environment Variables for Maven
1. Open **Environment Variables** (as explained in Step 1 for Java).
2. Add a new **System Variable**:
    - **Variable Name**: `MAVEN_HOME`
    - **Variable Value**: Path to the extracted Maven folder `(e.g., C:\Program Files\Maven)`.
3. Update the `Path` variable:
    - Find **Path** under **System Variables** and click **Edit**.
    - Add: **%MAVEN_HOME%\bin**.

### Step 4: Verify Installation

```
mvn -version
```

## 3. Install MySQL
### Step 1. Download MySQL
   1. Go to the MySQL Community Downloads page.
   2. Choose the latest **MySQL Community Server**.
   3. Select the appropriate version for Windows (x86, 64-bit).
   4. Click **Download.** (You can skip creating an account by clicking **No thanks, just start my download**.)
### Step 2.  Install MySQL
1. Run the Installer:
    - Locate the downloaded .msi file and double-click to launch the installer. 
2. Choose Setup Type:
    - Choose Developer Default (or Custom if you want more control over features).
3. Resolve Dependencies:
    - If the installer identifies missing dependencies, click Execute to install them (e.g., Visual Studio Redistributables).
4. Product Configuration:
    - Click Next to configure MySQL Server.
5. Select Server Configuration:
    - Choose Standalone MySQL Server.
    - Click Next.
6. Set Authentication Method:
    - Choose Use Legacy Authentication Method if needed for compatibility.
    - Otherwise, stick with Strong Password Encryption.
7. Create a Root Password:
    - Enter a strong root password and remember it.
    - Optionally, create additional MySQL users.
8. Configure Ports:
    - Default port is 3306. Ensure it’s open in your firewall.
    - Leave other settings as default.
9. Execute Installation:
    - The installer will set up the server. Click Execute to complete the process.

### Step 3. Add MySQL to PATH Environment Variable
1. Open **System Properties**:
    - Press `Win + S` → Search for **Environment Variables** → Click **Edit the system environment variables**.

2. Add MySQL’s bin folder to the system **Path** variable:
    - Find **Path** under System Variables and click **Edit**.
    - Add: `C:\Program Files\MySQL\MySQL Server 8.0\bin` (adjust path if MySQL was installed elsewhere).

4. Verify Installation
    ```
    mysql --version
    ```

### Step 5. Start MySQL Server
1. Open MySQL Workbench or MySQL Command Line Client.
2. Log in with the root user:
    ```
    mysql -u root -p
    ```
3. Test commands like
    ```sql
    SHOW DATABASES;
    ```


# Stage 3 : Deploy the app and database on AWS or Azure using Virtual Machines. Automate it via Bash provision scripts that work in user data.


## DB instance 
### Step 1 : Launch instance
- **Hardware**
    - Min 1 GB memory e.g. AWS t3a.micro or t3.micro or Azure B1s
- **Software**
    - Ubuntu 22.04 LTS (Can run on Windows 10/11 also)
    - MySQL database
    - Database must be seeded via an SQL script library.sql
- **Security Group:**
    - Inbound rules allow:
        - SSH (port 22) from a defined CIDR range.
        - MySQL (port 3306) from the application server's security group.
    - Outbound rule allows all traffic to any destination.


### Step 2: 
1. SSH into the instance 
   1. Update 
        ```
        sudo apt-get update -y
        ```
    2. Upgrade
        ```
        sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y
        ```
    3. Install MySQL Server
        ```
        sudo DEBIAN_FRONTEND=noninteractive apt-get install mysql-server -y
        ```
    4. Start the MySQL Service
        ```
        sudo systemctl start mysql.service
        ```
    5. Create MySQL User and Grant Privileges
        ```
        sudo mysql -ppassword -e "CREATE USER 'java-app'@'%' IDENTIFIED BY 'password'; GRANT ALL PRIVILEGES ON library.* TO 'java-app'@'%'; FLUSH PRIVILEGES;"
        ```
    6. Generate SQL Seed File
    
        ```bash
        nano library.sql 
        # copy the sql file
        ```
    7.  Execute SQL Seed File
        ```
        sudo mysql -ppassword -e "SOURCE ./library.sql"
        ```
    8. Verify Data in Authors Table
        ```
        sudo mysql -ppassword library -e "SELECT * FROM authors;"
        ```
    9.  Configure MySQL for Remote Access
        1.  Edit the MySQL configuration file:
            ```
            sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
            ```
        2. Find the line:
            ```
            bind-address = 127.0.0.1
            ```
        3. Change it to:
            ```
            bind-address = 0.0.0.0
            ```
        4. Save and exit the file (Ctrl + O, Enter, Ctrl + X).
        5. Restart MySQL to apply the changes:
            ```
            sudo systemctl restart mysql
            ```

Database provision script :
```bash
#!/bin/bash

# Echo statement to indicate the start of the update and upgrade process
echo "[UPDATE & UPGRADE PACKAGES]"

# Variables
DB_NAME="library"
DB_USER="..."
DB_PASS="..."
SQL_FILE="library.sql"


# Update package list
echo "Updating package list..."
sudo apt-get update -y

# Upgrade all installed packages
echo "Upgrading installed packages..."
sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y

# Install MySQL server (using Java 17 in the comment for clarity)
echo "Installing MySQL server..."
sudo DEBIAN_FRONTEND=noninteractive apt-get install mysql-server -y

# Start the MySQL service
echo "Starting MySQL service..."
sudo systemctl start mysql.service
sudo systemctl enable mysql


# Clone the GitHub repository
echo "Cloning the repository from GitHub..."
export GITHUB_TOKEN='insert token'
wget --header="Authorization: token 'insert token' " https://raw.githubusercontent.com/corinnai/library-java17-mysql-app/main/library.sql -O library.sql


# Import the SQL file if it exists
if [ -f "${SQL_FILE}" ]; then
    echo "Importing SQL file into ${DB_NAME}..."
    sudo mysql -u root -e  "source ${SQL_FILE}"
else
    echo "SQL file '${SQL_FILE}' not found. Skipping import."
fi

#  Login as root and configure database
echo "Setting up the database and user..."
sudo mysql -u root <<EOF
-- Create the database
CREATE DATABASE IF NOT EXISTS $DB_NAME ;

-- Create a new MySQL user
CREATE USER IF NOT EXISTS '$DB_USER'@'%' IDENTIFIED BY '$DB_PASS';

-- Grant privileges on the database to the user
GRANT ALL PRIVILEGES ON $DB_NAME.* TO '$DB_USER'@'%';

-- Apply changes
FLUSH PRIVILEGES;

-- Exit SQL
EOF

# Allow remote connections (if required)
echo "Configuring MySQL to allow remote connections..."
sudo sed -i "s/^bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/mysql.conf.d/mysqld.cnf

# Restart MySQL service to apply changes
echo "Restarting MySQL service..."
sudo systemctl restart mysql
```


## APP instance
### Step 1 : Launch instance
- **Hardware**
    - Min 2 GB memory e.g. AWS `t3.small` or Azure `B1ms`
- **Software**
    - `Ubuntu 22.04 LTS` (Can run on Windows 10/11 also)
    - Maven
    - Java 17
    - `ProjectLibrary2` folder is the "app" folder
    - App uses the following environment variables to connect to the database:
        - Variable name: `DB_HOST`
            - Description: Acts like a connection string
            - Value: `jdbc:mysql://$DATABASE_IP:3306/library`
        - Variable name: `DB_USER`
            - Description: The username setup in your MySQL database
            - Value: Can be whatever what you want to setup
        - Variable name: `DB_PASS`
            - Description: The password setup in your MySQL database
            - Value: Can be whatever what you want to setup
- **Security Group**:
    - Inbound rules allow:
        - SSH (port 22) from a defined CIDR range.
        - HTTP (port 5000) from the same CIDR range.
    - Outbound rule allows all traffic to any destination.

### Step 2: 
1. SSH into the instance:
    1. Update
        ```bash
        sudo apt-get update -y
        ```
    2. Upgrade
        ```bash
        sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y
        ```
    3.  Install Java 17
        ```bash
        sudo DEBIAN_FRONTEND=noninteractive apt install openjdk-17-jdk -y
        ```
    4. Set Java Home Environment Variable
        ```bash
        # Set Java home environment variable and update the PATH
        export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
        export PATH=$JAVA_HOME/bin:$PATH
        ```
    5. Install Maven
        ```bash
        # Install Maven by downloading and extracting the binary
        wget https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.tar.gz
        ```
        ```bash
        # Extract Maven to the /opt directory
        sudo tar -xvzf apache-maven-*.tar.gz -C /opt
        ```
        ```bash
        # Move extracted Maven to a more appropriate directory
        sudo mv /opt/apache-maven-* /opt/maven
        ```

    6.  Configure Maven Environment Variables
        ```bash
        # Export Maven environment variables
        export M2_HOME=/opt/maven
        export PATH=$M2_HOME/bin:$PATH
        ```
    7. Check Maven Installation
        ```bash
        mvn -version
        ```
    8. Clean Up Maven Download
        ```
        rm apache-maven-*.tar.gz
        ```
    9. Set Database Connection Variables
        ```bash
        export DB_USER="...."
        export DB_PASS="...."
        export DB_HOST="jdbc:mysql://<db-vm-private-ip>:3306/library"
        ```
    10. Clone the GitHub Repository
        ```bash
        export GITHUB_TOKEN=....
        ```
        ```bash
        git clone https://$GITHUB_TOKEN@github.com/corinnai/library-java17-mysql-app.git /home/ubuntu/library-app
        ```
    11. Navigate to the Project Directory
        ```
        cd /home/ubuntu/library-app/LibraryProject2
        ```
    12. Build the Project
        ```
        mvn clean package
        ```
        - **If tests fail during the package phase, you can skip them to proceed with the build:**
        ```
        mvn clean package -DskipTests
        ```
    13.  Start the Spring Boot Application
            ```
            mvn spring-boot:start
            ```
 

Application provision script :
```bash
#!/bin/bash

# Echo statement to indicate the start of the script
echo "[STARTING APPLICATION PROVISIONING]"

# Update and upgrade packages
echo "[UPDATE & UPGRADE PACKAGES]"
sudo apt-get update -y
sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y

# Install Java 17
echo "Installing Java 17..."
sudo DEBIAN_FRONTEND=noninteractive apt install openjdk-17-jdk -y

# Install Maven
sudo DEBIAN_FRONTEND=noninteractive apt install -y maven

# Verify Maven installation
echo "Verifying Maven installation..."
mvn -version

export DB_USER="..."
export DB_PASS="..."
export DB_HOST="jdbc:mysql://'db-ec2-private-instance'/library"

# Clone the GitHub repository
echo "Cloning the repository from GitHub..."
export GITHUB_TOKEN='insert token'
git clone https://$GITHUB_TOKEN@github.com/corinnai/library-java17-mysql-app.git /home/ubuntu/library-app
unset GITHUB_TOKEN

# Navigate to the application directory
echo "Navigating to the application directory..."
cd /home/ubuntu/library-app/LibraryProject2

# Wait for the database to be ready
echo "Waiting for the database to initialize..."
sleep 5s

#  Build the project using Maven
mvn clean package -DskipTests

# Start the Spring Boot application
echo "Starting the Spring Boot application..."
mvn spring-boot:start

# Final message indicating script completion
echo Application setup and start completed.
```

**To check the logs SSH into EC2**
```bash
tail -f /var/log/cloud-init-output.log
```

**BLOCKER:**

`java.sql.SQLException: Access denied for user 'corina'@'ip-172-31-63-190.eu-west-1.compute.internal' (using password: YES)`
- because in my script i had **BD_PASSWORD** instead of **DB_PASS**



# Stage 4  Deploy the app and database on AWS or Azure using containers running on a Virtual Machine (Docker Compose). Automate it via Bash provision scripts that work in user data. 
1. For Stage 4 above:
    - Bash provision script for a single VM that runs in user data but deploys the app and database using containers on the one machine. The containers run by the script should use Docker images already uploaded to Docker Hub.
    -  Docker-related files
        -  Dockerfile files 
        -  Docker-compose YAML file
        -  Dockerised application images built and ready for deployment





## Step 1: Prepare the Environment
1. **Install Docker on Your PC**: If you don't already have Docker installed, download and install it from Docker's official website: (https://www.docker.com/)
2. **Verify Docker Installation:** Run the following command to ensure Docker is installed correctly:
    ```bash
    docker --version
    ```


## Step 2: Build the JAR File Locally
### Step 1: Install Maven
1. **Download Maven**:
   - Go to the Maven Downloads Page and download the latest binary zip file (e.g., apache-maven-"version"-bin.zip).
2. **Extract the Zip File:**
     - Extract the downloaded zip file to a directory, for example:
        ```makefile
        C:\Program Files\Apache\Maven
        ```
3. **Set Up Environment Variables:**
    - Open **Environment Variables**:
        - Right-click on "This PC" or "My Computer".
        - Select **Properties > Advanced System Settings > Environment Variables**.
4. Add Maven's bin directory to the **Path** variable:
    - In **System Variables**, find Path and click **Edit**.
    - Add:
        ```makefile
        C:\Program Files\Apache\Maven\bin
        ```
    - Add a new environment variable for Maven:
        - Variable Name: MAVEN_HOME
        - Variable Value: C:\Program Files\Apache\Maven

5. **Verify Maven Installation**:
    - Open a new terminal and run:
        ```bash
        mvn -version
        ```

### Step 2: Install JDK
1. **For Windows**:
    - Download the latest JDK (Java 17 or above) from Oracle JDK Downloads or Adoptium. : https://www.oracle.com/java/technologies/downloads/?er=221886
    - Install the JDK and note the installation directory `(e.g., C:\Program Files\Java\jdk-17)`.
  
2. **Set Up Environment Variables**:
    - Add the JDK's `bin` directory to the `Path` variable
        - Go to **Environment Variables** (as explained earlier).
        - In **System Variables**, find `Path` and add:
            ```makefile
            C:\Program Files\Java\jdk-17\bin
            ```
        - Set the JAVA_HOME variable:
            - Variable Name: JAVA_HOME
            - Variable Value: C:\Program Files\Java\jdk-17
3. Verify JDK Installation: Open a new terminal and run:
    ```bash
    javac -version
    ```


### Step 3 : Install MySQL(dont need - used docker compose)
1. Download the MySQL installer from the `official MySQL website`.https://dev.mysql.com/downloads/installer/.
2. Download the **MySQL Installer for Windows**:
    - Choose **MySQL Installer (Community)**.
    - Select the "Web" or "Full" version.
        - The "Web" version downloads the required components during installation.
        - The "Full" version includes everything in the installer.

3. Save the installer to your computer.
4.  Run the Installer:
    1.  Double-click the downloaded .msi file to run the MySQL Installer.
    2.  Choose the setup type:#
        - **Developer Default:** Installs MySQL Server, Workbench, and additional tools.
        - **Server Only**: Installs only the MySQL Server.
        - **Custom:** Allows you to select specific components.
        - **Full:** Installs all available MySQL products.
    3. Click **Next** and let the installer check for prerequisites.

5. Install MySQL Server
    1. **Product Configuration**:
        - The installer will list the products to be installed. Confirm and click Execute to start downloading and installing the selected products.
    2. **Server Configuration**:
        - Choose a setup type:
            - **Standalone MySQL Server (most common)**.
        - Select a port (default: **3306**).
        - Click **Next**.
    3. **Authentication Setup**:
        - Set the **root password** (important—do not forget this password).
        - Optionally, create additional MySQL users if needed.
    4. **Windows Service Configuration**:
        - Configure MySQL to run as a Windows service (recommended).
        - Keep the default service name (e.g., `MySQL` or `MySQL80`).
        - Choose whether to start the service automatically.

6. Complete the Installation
   1. The installer will apply the configuration and start the MySQL service
   2. Click **Finish** to complete the installation.

7. Add `bin` folder to the `PATH` 
    ```makefile
    C:\Program Files\MySQL\MySQL Server 8.0\bin
    ```
8. Verify Installation
    1. Open a Command Prompt and type:
        ```
        mysql --version
        ```


### Step 4: Building with Maven
1. Navigate to your project directory:
    ```bash
    cd ~/OneDrive/Documents/github/library-java17-mysql-app/LibraryProject2
    ```

2. Run Maven again:
    ```bash
    mvn clean package -DskipTests
    ```


## Dockerfile
### Step 1 : 
1. Navigate to the root directory of your project `(LibraryProject2)`.
2. Create a new file named `Dockerfile` in the directory:
    ```bash
    nano Dockerfile
    ```
3. Add the following content to the Dockerfile:
    ```dockerfile
    # Use OpenJDK as the base image
    FROM openjdk:17-jdk-slim

    # Set the working directory inside the container
    WORKDIR /app

    # Copy the JAR file from the target directory to the container
    COPY target/LibraryProject2-0.0.1-SNAPSHOT.jar app.jar

    # Expose the port the app runs on
    EXPOSE 5000

    # Set the entrypoint to run the application
    ENTRYPOINT ["java", "-jar", "app.jar"]
    ```
4. Save and Exit: Save the `Dockerfile` and exit.

### Step 2: Build the Docker Image
1. Navigate to the directory containing the `Dockerfile`:
    ```bash
    cd ~/OneDrive/Documents/github/library-java17-mysql-app/LibraryProject2
    ```
2. Build the Docker image:
    ```bash
    docker build -t corinnai/library-java-springboot:latest .
    ```
3. Verify the Docker Image
    ```bash
    docker images
    ```

4.  Push to Docker Hub Ensure you are logged in to Docker Hub:
    ```bash
    docker login
    docker push corinnai/library-java-springboot:latest
    ```



## Database SQL Seeding

Create a file named `library.sql` to seed the MySQL database:
    ```sql
    DROP DATABASE IF EXISTS library;
    CREATE DATABASE library;
    USE library;

    CREATE TABLE authors (
    author_id int PRIMARY KEY NOT NULL AUTO_INCREMENT,
    full_name VARCHAR(40)
    );
    CREATE TABLE books (
    book_id int  PRIMARY KEY NOT NULL AUTO_INCREMENT,
    title VARCHAR(100),
    author_id int,
    FOREIGN KEY (author_id) REFERENCES authors(author_id)
    );

    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Phil');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('William Shakespeare');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Jane Austen');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Charles Dickens');
    ```


## Create the `docker-compose.yml` file 
1. Create the `docker-compose.yml`
    ```yaml
        version: '3'

        services:
        # Define the database service
        database:
            image: mysql:8.0  
            environment:  
            MYSQL_DATABASE: library 
            MYSQL_ROOT_PASSWORD: root  
            volumes:  
            - mysql-data:/var/lib/mysql  
            - ./library.sql:/docker-entrypoint-initdb.d/library.sql  
            
            ports:
            - "3306:3306"  
            healthcheck:  
            test: ["CMD", "mysqladmin", "ping", "-h", "localhost", "-proot"]  
            interval: 10s  
            timeout: 5s  
            retries: 3  

        # Define the application service (Spring Boot app)
        application:
            image: corinnai/library-java-springboot 
            container_name: spring-app  
            depends_on:  
            database:
                condition: service_healthy  
            environment:  
            - DB_HOST=jdbc:mysql://database:3306/library  
            - DB_USER=root  
            - DB_PASS=root  
            ports:
            - "5000:5000"  

        volumes:
        mysql-data:  
    ```

2. Build the container
    ```bash
    docker-compose up -d
    ```

3. Remove the container
    ```bash
    docker-compose down -v
    ```

## Launching an EC2 instance

### Step 1: Prepare the Virtual Machine
1. **Launch a Virtual Machine:**
    - **AWS**: Use an EC2 instance (e.g., t3.small) with Ubuntu 22.04 LTS.
    - **Security group:**
      - SSH
      - HTTP : 5000
      - MySQL/Aurora: 3306
      - ICMP : -1(all)- optional for ping ( test connectivity)

2. **Connect to the VM**:
    - SSH into the instance 

3. **Update and Install Prerequisites**:
    ```bash
    sudo apt-get update -y
    sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y
    sudo DEBIAN_FRONTEND=noninteractive apt-get install docker.io  docker-compose -y
    ```

4. **Enable Docker Service**:
    ```bash
    sudo systemctl enable docker
    sudo systemctl start docker
    ```

5. **Verify Docker Installation**:
    ```bash
    docker --version
    docker-compose --version
    ```

### Step 2: Prepare Docker-Related Files
1.  **Create a Project Directory**:
    ```bash
    mkdir ~/library-docker
    cd ~/library-docker
    ```

2. **Create the library.sql**
    ```bash
    sudo nano library.sql
    ```
    ```sql
    DROP DATABASE IF EXISTS library;
    CREATE DATABASE library;
    USE library;

    CREATE TABLE authors (
    author_id int PRIMARY KEY NOT NULL AUTO_INCREMENT,
    full_name VARCHAR(40)
    );
    CREATE TABLE books (
    book_id int  PRIMARY KEY NOT NULL AUTO_INCREMENT,
    title VARCHAR(100),
    author_id int,
    FOREIGN KEY (author_id) REFERENCES authors(author_id)
    );

    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Phil');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('William Shakespeare');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Jane Austen');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Charles Dickens');
        
    ```


3. **Create docker-compose.yml**

    ```bash
    sudo nano docker-compose.yml
    ```
    ```yaml
    version: '3'

    services:
    # Define the database service
    database:
        image: mysql:8.0  
        environment:  
        MYSQL_DATABASE: library 
        MYSQL_ROOT_PASSWORD: root  
        volumes:  
        - mysql-data:/var/lib/mysql  
        - ./library.sql:/docker-entrypoint-initdb.d/library.sql  
        
        ports:
        - "3306:3306"  
        healthcheck:  
        test: ["CMD", "mysqladmin", "ping", "-h", "localhost", "-proot"]  
        interval: 10s  
        timeout: 5s  
        retries: 3  

    # Define the application service (Spring Boot app)
    application:
        image: corinnai/library-java-springboot 
        container_name: spring-app  
        depends_on:  
        database:
            condition: service_healthy  
        environment:  
        - DB_HOST=jdbc:mysql://database:3306/library  
        - DB_USER=root  
        - DB_PASS=root  
        ports:
        - "5000:5000"  

    volumes:
    mysql-data:  
    ```

4. **Build the container**

    ```bash
    sudo docker-compose up -d
    ```
5. **Check running containers**
    ```
    sudo docker ps 
    ```
6. **Remove container** 
    ```bash
    sudo docker-compose down -v 
    ```


## Create a Provisioning Script

1. **Create the Script** On your local machine, create a file named `provision.sh:`
    ```bash
    sudo nano provision.sh
    ```

2. Add the following :
    ```bash
    #!/bin/bash

    # Echo statement to indicate the start of the update and upgrade process
    echo "[UPDATE & UPGRADE PACKAGES]"

    # Update package list
    echo "Updating package list..."
    sudo apt-get update -y

    # Upgrade all installed packages
    echo "Upgrading installed packages..."
    sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y


    echo "[DOCKER]: Installing Docker"
    sudo DEBIAN_FRONTEND=noninteractive apt-get install docker.io  docker-compose -y


    echo "[DOCKER]: Enabling Docker"
    sudo systemctl enable docker

    echo "[DOCKER]: Starting Docker"
    sudo systemctl start docker

    echo "[DOCKER]: Provisioning Complete."
    sudo docker --version

    mkdir /home/ubuntu/app
    cd /home/ubuntu/app


    # Write library.sql
    cat <<'EOF' > library.sql
    DROP DATABASE IF EXISTS library;
    CREATE DATABASE library;
    USE library;

    CREATE TABLE authors (
    author_id int PRIMARY KEY NOT NULL AUTO_INCREMENT,
    full_name VARCHAR(40)
    );
    CREATE TABLE books (
    book_id int  PRIMARY KEY NOT NULL AUTO_INCREMENT,
    title VARCHAR(100),
    author_id int,
    FOREIGN KEY (author_id) REFERENCES authors(author_id)
    );

    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Phil');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('William Shakespeare');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Jane Austen');
    INSERT INTO `library`.`authors` (`full_name`) VALUES ('Charles Dickens');
    EOF

    # Write docker-compose.yml
    cat <<'EOF' > docker-compose.yml
    version: '3'

    services:
    # Define the database service
    database:
        image: mysql:8.0  
        environment:  
        MYSQL_DATABASE: library 
        MYSQL_ROOT_PASSWORD: root  
        volumes:  
        - mysql-data:/var/lib/mysql  
        - ./library.sql:/docker-entrypoint-initdb.d/library.sql  
        ports:
        - "3306:3306"  
        healthcheck:  
        test: ["CMD", "mysqladmin", "ping", "-h", "localhost", "-proot"]  
        interval: 10s  
        timeout: 5s  
        retries: 3  

    # Define the application service (Spring Boot app)
    application:
        image: corinnai/library-java-springboot 
        container_name: spring-app  
        depends_on:  
        database:
            condition: service_healthy  
        environment:  
        - DB_HOST=jdbc:mysql://database:3306/library  
        - DB_USER=root  
        - DB_PASS=root  
        ports:
        - "5000:5000"  

    volumes:
    mysql-data:  
    EOF

    sudo usermod -aG docker $USER
    cd /home/ubuntu/app

    # Start the Docker containers
    sudo docker-compose up -d

    ```