# SSH Keys Overview

SSH keys provide secure authentication for accessing your GPU instances on Nebula Block. Instead of using passwords, SSH key pairs offer a more secure and convenient way to connect to your instances.

## What are SSH Keys?

SSH keys come in pairs:
- **Public Key**: Stored on Nebula Block and added to your instances
- **Private Key**: Kept securely on your local machine

This system provides several advantages:
- More secure than password authentication
- No need to remember or type passwords
- Protection against brute-force attacks
- Automated script and tool authentication

## Key Features

- **Easy Management**: Add, remove, and manage keys through our dashboard
- **Multiple Keys**: Add different keys for different instances or team members
- **Instant Application**: New keys are immediately available for use
- **Cross-Platform**: Works with all major operating systems
- **Standard Format**: Compatible with industry-standard SSH tools

## Prerequisites

- A Nebula Block account
- Basic understanding of SSH concepts
- SSH client installed on your local machine

## Common Use Cases

1. **Remote Instance Access**
   - Securely connect to GPU instances
   - Run commands and manage resources
   - Transfer files between local and remote systems

2. **Automated Deployments**
   - Use in CI/CD pipelines
   - Automate instance management
   - Secure script execution

3. **Team Collaboration**
   - Share instance access securely
   - Manage team member access
   - Track key usage

For step-by-step instructions on creating and using SSH keys, see our [Quickstart Guide](Quickstart.md). 