# isec6000-assignment1-task1

## Set Up Initial Infrastructure

### 1. Create a Kubernetes Cluster on GKE

a. Log in to your [Google Cloud Console][googlelink].

[googlelink]: https://cloud.google.com/cloud-console/?utm_source=google&utm_medium=cpc&utm_campaign=japac-AU-all-en-dr-BKWS-all-super-trial-PHR-dr-1605216&utm_content=text-ad-none-none-DEV_c-CRE_648976003582-ADGP_Hybrid%20%7C%20BKWS%20-%20BRO%20%7C%20Txt%20~%20Management%20Tools_Cloud%20Console_google%20cloud%20console_main-KWID_43700076166781865-aud-1644542956308%3Akwd-296393718382&userloc_9070531-network_g&utm_term=KW_google%20cloud%20console&gclid=EAIaIQobChMItqrAjLucgQMV7RF7Bx39ugg8EAAYASAAEgKtWfD_BwE&gclsrc=aw.ds "Go google"

b. Navigate to the Kubernetes Engine section and click "Create Cluster."
![dev](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/2b1367e5-5acf-4ec9-8786-295c8bfae02d)

c. Configure your cluster settings, such as the cluster name, location, and node pool configuration.
![dev2](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/c23bbd5e-2a1f-4f14-a64d-65dffc5dae27)

d. Choose the desired Kubernetes version.

e. Click "Create" to provision your GKE cluster.

### 2. Install and configure kubectl to manage your Kubernetes cluster.

a. After creating the GKE cluster, you will need to configure your local environment
to use kubectl to interact with this cluster.

b. In the Google Cloud Console, navigate to the "Kubernetes Engine" > "Clusters"
section and click the "Connect" button next to your cluster.

c. Follow the instructions to authenticate kubectl with your GKE cluster.

    gcloud container clusters get-credentials <cluster name> --region us-central1 --project <project name>

![dev3](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/bc4e9f61-3471-42d3-8fed-fc641fb28bf0)

### 3. Set up a private GitHub repository to store your project files.

a. Log in to your [GitHub](https://github.com) account (or create one if you don't have it).

b. Click on the '+' icon at the top right corner of the GitHub dashboard and select
"New repository."

c. Choose a meaningful repository name for your ISEC6000 Secure DevOps project.

d. Select "Public" for the repository visibility.

e. You need to add a description and choose whether to initialize the repository
with a README.

f. Click "Create repository."
g. Push the initial setup code to the repository and update your README.
[MDfile_direction](https://www.w3schools.io/file/markdown-folder-tree/)

g. tag isec6000-assignment1-task1 using below command

    git tag isec6000-assignment1-task1

then, push it to your github

    git push origin isec6000-assignment1-task1

---

### 2. Microservices Architecture and Deployment

a. Fork the Saleor platform repository

- When I forked the Saleor-platform repository, I chose to fork all branches, including the main one. I did this because I needed the Docker Compose configuration file in the frontend-backend dependencies branch. However, I noticed that when I ran 'docker compose up' on the main branch, it only started the backend, leaving the frontend unresponsive. To solve this, I created a separate fork for the frontend code. To keep things organized and easy to reference, I tagged both forks with the label 'isec6000-assignment1-task2.' This approach allowed me to use the specific Docker Compose configuration from the frontend-backend dependencies branch while maintaining the ability to manage the backend and frontend components separately.

Below links are my repositories forked from saleor:

https://github.com/SuinChoi/saleor-platform
https://github.com/SuinChoi/react-front

To clone files in the repository, you can use below commands.

        git clone https://github.com/SuinChoi/saleor-platform
        git clone https://github.com/SuinChoi/react-front

Or if you want to clone specific branch:

        git clone -b <branch name> <repository url>

b. Deployment of Saleor Stack

- In both repositories have each docker-compose.yml file
- I changed the port from 3000 to 3009 on react-front
- I changed the port from 9000 to 9003 on saleor-platform
  ![Screenshot from 2023-09-07 14-51-38](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/25681557-0b7b-416e-b1e3-329f2022439c)
  ![Screenshot from 2023-09-07 14-54-36](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/665f1b91-f2c8-4b30-b606-bd4a63b6f752)
- Each repository, use follow command to deploy

        docker compose up

- The following screenshots depicing the operation uder the altered ports. In the case of the frontend, a recurring issue is the appearance of a '500 Error.' It is noteworthy that this issue is not isolated to my experience; several other students have also encountered the same display.

![Screenshot from 2023-09-07 14-55-36](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/b6267d93-593f-4e29-bab2-bec758be465a)
![Screenshot from 2023-09-07 15-24-52](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/84118a92-66ec-4417-9634-04901f1271e5)

c. Push modified file and Tag

        git add .
        git status
        git commit -m "meaningful message"
        git tag isec6000-assignment-task2
        git push origin main
        git push origin isec6000-assignment1-task2

---

### 3.Implementing Security Measures

a. install trivy

        wget https://github.com/aquasecurity/trivy/releases/download/v0.18.3/trivy_0.18.3_Linux-64bit.deb
        sudo dpkg -i trivy_0.18.3_Linux-64bit.deb

b. A trivy.yaml configuration file is essential for tailoring Trivy's container image scanning to your
specific security needs. It allows you to:

1.  Set Severity Levels: Define which vulnerabilities to prioritize based on severity, aligning
    with your risk tolerance.
2.  Control Secret Scanning: Enable or disable secret scanning to suit your security policies and application requirements.
3.  Optimize Performance: Configure caching options to speed up scans while ensuring you
    have the latest security data.
4.  Specify Database Source: Choose trusted sources for vulnerability databases.
5.  Ensure Consistency: Maintain uniform security configurations across environments and
    stages of development.
6.  Documentation and Auditing: Document your scanning settings for reference and audit
    trail purposes.

To make file, you can use vim

        vim trivy.yaml

and type the below contents in trivy.yaml file

![캡처1](https://github.com/SuinChoi/isec6000-assignment1-task1/assets/30892803/86b83f8b-9ea2-4d50-a6d1-40df0b67acfd)

b. Executing Trivy Container Image Vulnerability Scans with Custom Configuration

        trivy image -f json -o results.json -c /path/to/trivy.yaml <image-name>

the above command performs a container image vulnerability scan using Trivy with specific
configurations from a trivy.yaml file. Here's a brief explanation of each part of the command: <br>
trivy image: Initiates a Trivy scan for a container image.<br>
-f json: Specifies the output format for the scan results as JSON.<br>
-o results.json: Specifies the output file where the scan results will be saved in JSON format (you can choose a different filename if needed).<br>
-c /path/to/trivy.yaml: Points to the location of your trivy.yaml configuration file, allowing you to
customize scan settings.<br>
image-name: Replace this with the name of the container image you want to scan.

