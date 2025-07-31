
# AWS CLI Installation and Configuration Guide

This tutorial helps you understand how to install and configure AWS CLI on EC2 instances with easy-to-follow steps.

---

## Prerequisites

- **EC2 Instance** launched in AWS
- Properly configured **security groups** and **SSH key pairs**
- Basic knowledge of Linux command line

> **Note:** For detailed EC2 instance launch instructions, refer to the dedicated tutorial.

---

## Step-by-Step Installation Guide

### 1. Connect to Your EC2 Instance

Connect to your EC2 instance using either:
- **PuTTY** (Windows)
- **Command Prompt/Terminal** (Windows/Mac/Linux)

> For detailed connection instructions, check the connection tutorials.

---

### 2. Update Package List

```bash
sudo apt update
```
<img width="1470" height="883" alt="image" src="https://github.com/user-attachments/assets/1344da6a-4e5b-4a57-9fbd-2efcd2203524" />
<img width="1090" height="523" alt="image" src="https://github.com/user-attachments/assets/b16f3303-6900-4917-b5bd-0619fe478cc4" />

---

### 3. Install AWS CLI

**Option A: Follow Official AWS Documentation**

For the most reliable and up-to-date installation method, refer to the [Official AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

**Option B: Quick Installation Commands**
<img width="1090" height="187" alt="image" src="https://github.com/user-attachments/assets/463713a2-f6ce-402e-85e7-7b5341ae027b" />

```bash
# Download AWS CLI v2
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

# Unzip the installer
unzip awscliv2.zip

# Install AWS CLI
sudo ./aws/install
```

---

### 4. Verify Installation

```bash
# Check AWS CLI version
aws --version
```

You should see output similar to:
```
aws-cli/2.x.x Python/3.x.x Linux/x.x.x exe/x86_64.x
```

---

### 5. Obtain AWS Access Keys

1. Open the **AWS Management Console**
2. Navigate to **Security Credentials** (click on your username in top-right)
3. Go to **Access Keys** section
4. Click **Create Access Key**
5. **Download the credentials file** (keep it secure!)

---

### 6. Configure AWS CLI

Run the configuration command:

```bash
aws configure
```
<img width="1090" height="399" alt="image" src="https://github.com/user-attachments/assets/4494ef9a-563d-4320-bf79-798d3bf5d1e8" />

You'll be prompted to enter the following information:

```
AWS Access Key ID [None]: [Enter your Access Key ID]
AWS Secret Access Key [None]: [Enter your Secret Access Key]
Default region name [None]: [Enter your preferred region, e.g., us-east-1]
Default output format [None]: json
```

---

### 7. Test Your Configuration

```bash
# Test AWS CLI configuration
aws sts get-caller-identity
```

If configured correctly, you should see output showing your account details:

```json
{
    "UserId": "AIDACKCEVSQ6C2EXAMPLE",
    "Account": "123456789012",
    "Arn": "arn:aws:iam::123456789012:user/your-username"
}
```

---

## Configuration Files Location

Your AWS credentials and configuration are stored in:

```
~/.aws/credentials    # Contains access keys
~/.aws/config        # Contains region and output format
```

---

## Security Best Practices

### ✅ Do's
- **Keep credentials secure** - Never share or commit access keys to version control
- **Use IAM roles** when possible instead of access keys
- **Rotate access keys** regularly
- **Use least privilege principle** - Grant only necessary permissions

### ❌ Don'ts
- **Never hardcode** access keys in scripts or applications
- **Don't use root account** access keys
- **Avoid** sharing credentials via email or chat

---

## Common Commands

```bash
# List S3 buckets
aws s3 ls

# Describe EC2 instances
aws ec2 describe-instances

# List IAM users
aws iam list-users

# Get current configuration
aws configure list
```

---

## Troubleshooting

### Issue: "Command not found: aws"
**Solution:** Ensure AWS CLI is properly installed and added to PATH.

### Issue: "Unable to locate credentials"
**Solution:** Run `aws configure` to set up your credentials.

### Issue: "Access Denied" errors
**Solution:** Check if your IAM user has the necessary permissions for the operation.

### Issue: "Invalid credentials"
**Solution:** Verify your access keys are correct and haven't been rotated/disabled.

---

## Multiple Profiles (Optional)

If you need to work with multiple AWS accounts or regions:

```bash
# Configure a named profile
aws configure --profile myprofile

# Use a specific profile
aws s3 ls --profile myprofile

# Set default profile
export AWS_PROFILE=myprofile
```

---

## Updating AWS CLI

To update to the latest version:

```bash
# Download and install latest version
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install --update
```

---

## Next Steps

Now that AWS CLI is configured, you can:
- Automate AWS resource management
- Create deployment scripts
- Integrate with CI/CD pipelines
- Use AWS services programmatically

---

## References

- [AWS CLI Official Documentation](https://docs.aws.amazon.com/cli/)
- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/)
- [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)

---

**🎉 Congratulations!** You've successfully installed and configured AWS CLI on your EC2 instance.

For more AWS tutorials and guides, check out the other documentation in this repository.
