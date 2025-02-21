
# Quickstart

## Log In or Sign Up
- If you have an account, log in with Google or email/password.
- If you’re new to Nebula Block, create an account for free.

## Create a GPU Instance
- Choose a Location
  - Select the preferred region for your instance to optimize performance and minimize latency.
- Select Hardware Configuration
  - Choose from the available GPU options:
    - NVIDIA H100: Best for large-scale AI model training.
    - NVIDIA A100: Ideal for AI/ML workloads and data analytics.
    - NVIDIA L40s: Balanced performance for AI inference and graphics workloads.
    - RTX A6000: Great for 3D rendering, simulations, and visualization.
    - RTX 4090: 
- Choose an Operating System/Image
- Select an SSH Public Key (if applicable)
  - Create or select an existing SSH public key for secure access to the instance.
  - Note that some instances may not support SSH Public Keys yet, in which case a secure username and password will be 
  - provided to you.
- Set a Server Name
  - Assign a meaningful name to your instance for easy identification.
- Deploy
  - Review your configuration and click "Deploy". Your instance will be provisioned and ready within minutes.

## Connect to Your GPU Instance

##### SSH Key Authentication 

Once your instance is running, connect to it using SSH:
```bash
ssh -i /path/to/your/private/key username@instance-ip
```
- Replace `/path/to/your/private/key` with the path to your private SSH key.
- Replace `username` with the username of your instance, and replace `instance-ip` with the public IP Address of your 
instance. You can find the username and Public IP Address information in your instance detail page.

##### Password Authentication 

Once your instance is running, connect to it using SSH:
```bash
ssh username@instance-ip
```

- You'll then be prompted for your password. Simply enter it and press Enter. 
- Replace `username` with the username of your instance, and replace `instance-ip` with the public IP Address of your 
instance. 
- You can find the username, password and Public IP Address in your instance detail page.

## Manage Your Instance
- Access the Dashboard
  - Use the Instances section in your Nebula Block dashboard to view all active instances.
  - Click "View" button to view the details of the instance.
- Actions 
  - User the dashboard controls to manage instance states: Power on, Power off, Reboot or Terminate Instances (note that
some instances may only support the Terminate action). 
