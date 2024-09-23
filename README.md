# Ask-to-set-project-before-executing-the-gcloud-command-on-terminal
Terminal pop mesg to select right project before executing any gcloud command. 


    To ensure that your terminal prompts you to enter the correct project every time you run a gcloud command, you can create a custom wrapper for gcloud that will always ask for the project ID before running any gcloud command. Here’s how you can achieve this:
    
Steps to Implement:
    
    Create a wrapper script to replace the default gcloud command with a custom script.
    
    Move the original gcloud command and point the new script to it after confirming the project.
    
Example Implementation:
    
    Backup the original gcloud binary (optional but recommended):
    

    mv $(which gcloud) $(which gcloud)_original
    Create a new script (let's call it gcloud) and place it in a directory in your PATH (such as /usr/local/bin/ if it has higher precedence in your shell $PATH):
    
 
    sudo nano /usr/local/bin/gcloud

Add the following script into this file:
    
    #!/bin/bash
    
    # Prompt for the project ID
    read -p "Please enter the correct Google Cloud Project ID: " PROJECT_ID
    
    # Set the project in gcloud config
    gcloud_original config set project "$PROJECT_ID"
    
    # Pass through all other gcloud arguments
    gcloud_original "$@"

Make the script executable:

    sudo chmod +x /usr/local/bin/gcloud

## 2nd way Solution

    Add this into the ~/.bashrc.

    cat ~/.config/gcloud/configurations/config_default

    benefits:

    Every time you open the terminal, it will automatically display which project your terminal has access to.
