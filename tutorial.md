# Cloud Ops Agent Ansible Tutorial
## Prerequisites
In order to use Ansible to install the Cloud Ops Agent you must:
1. Have a service account available for Ansible to query the inventory
2. Be able to ssh to the systems and have escalation priviledges to install packages

## Service Account Setup 
First, login to your gcp account within cloudshell, this ensures you're able to run the necessary commands
```bash
gcloud auth login
```
Continue by setting your project ID to the project you'd like to work within. This project should have existing VMs available to run the Ansible playbook against:
```bash
gcloud config set project PROJECT_ID
```
Next you'll need to create a service account and credentials file. These resources allow configuration management tools to query and return the inventory from GCP dynamically. By using the `roles/compute.viewer` role, this credential can only view and compute resources and cannot modify any parts of the GCE system.
1. Create the service account.
```bash
gcloud iam service-accounts create SERVICE_ACCOUNT_ID --description="DESCRIPTION" --display-name="DISPLAY_NAME"
```
2. Create the iam policy binding and attach the necessary role to the account:
```bash 
gcloud projects add-iam-policy-binding PROJECT_ID --member="serviceAccount:SERVICE_ACCOUNT_ID@PROJECT_ID.iam.gserviceaccount.com" --role="roles/compute.viewer"
```
3. Create the key-file associated with the service account:
```bash
gcloud iam service-accounts keys create key-file --iam-account=sa-name@project-id.iam.gserviceaccount.com
```

## SSH Setup
If you have an SSH key that works for the GCE instances in this project, you can upload it to cloudshell using the *Upload File* tool in the
<walkthrough-editor-spotlight cssSelector="mat-focus-indicator mat-menu-trigger mat-tooltip-trigger large mat-icon-button mat-button-base">more tools menu</walkthrough-editor-spotlight>

## Install the Cloud Ops Agent Ansible Role

Install the Ansible role:
```bash
ansible-galaxy install git+https://github.com/GoogleCloudPlatform/google-cloud-ops-agents-ansible.git
```

### Define Your Playbook

Part one instructions.

### Part 2

Part two instructions.

## Conclusion

Done!
