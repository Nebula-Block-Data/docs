# SSH Keys Quickstart Guide

This guide will walk you through creating and using SSH keys with your Nebula Block GPU instances.

## 1. Generate an SSH Key Pair

### On Linux/macOS
```bash
# Generate a key pair (replace your@email.com with your email)
ssh-keygen -t ed25519 -C "your@email.com"

# Start the ssh-agent
eval "$(ssh-agent -s)"

# Add your private key to ssh-agent
ssh-add ~/.ssh/id_ed25519
```

### On Windows (PowerShell)
```powershell
# Generate a key pair
ssh-keygen -t ed25519 -C "your@email.com"

# Start the ssh-agent
Start-Service ssh-agent

# Add your private key to ssh-agent
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

## 2. Add Your Public Key to Nebula Block

1. Go to the [Nebula Block Dashboard](https://dashboard.nebulablock.com)
2. Navigate to SSH Public Key
3. Click "Create"
4. Copy your public key content:
   ```bash
   # On Linux/macOS
   cat ~/.ssh/id_ed25519.pub
   
   # On Windows
   type $env:USERPROFILE\.ssh\id_ed25519.pub
   ```
5. Paste the key content and give it a descriptive name
6. Click "Confirm"

## 3. Use SSH Keys with GPU Instances

### When Creating a New Instance
1. Start creating a new GPU instance
2. In the instance creation form, select your SSH key
3. Complete the instance creation

### Connect to Your Instance
```bash
# Replace with your instance's IP address
ssh -i ~/.ssh/id_ed25519 user@instance_ip
```

## 4. Best Practices

- Keep your private key secure and never share it
- Use a strong passphrase when generating keys
- Use different keys for different purposes
- Regularly rotate your keys
- Remove unused keys from your account

## 5. Troubleshooting

### Common Issues

1. **Permission Issues**
```bash
# Fix private key permissions
chmod 600 ~/.ssh/id_ed25519
```

2. **Connection Refused**
- Verify the instance is running
- Check if the IP address is correct
- Ensure the security group allows SSH (port 22)

3. **Key Not Working**
- Verify you're using the correct key
- Check if the key is added to the ssh-agent
- Ensure the public key is properly added to the instance

For more detailed information about SSH keys, see our [Overview](Overview.md).
