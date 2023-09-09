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
- - -

### 2. Install and configure kubectl to manage your Kubernetes cluster.

a. After creating the GKE cluster, you will need to configure your local environment
to use kubectl to interact with this cluster.

b. In the Google Cloud Console, navigate to the "Kubernetes Engine" > "Clusters"
section and click the "Connect" button next to your cluster.

c. Follow the instructions to authenticate kubectl with your GKE cluster.

    gcloud container clusters get-credentials <cluster name> --region us-central1 --project <project name>
- - -

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
