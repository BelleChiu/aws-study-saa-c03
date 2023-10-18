# AWS Configuration
## how to generate access keys in account

1. Login AWS web site

2. Click AWS account -> "Security Credientials"
(Note: type "IAM" in the search button and press "Enter" button)

3. Press "create access key" under "Access keys" in "AWS IAM credentials" tag

4. Choose the case for why you want to create an access key. We choose "Command Line Interface(CLI)"
    - Description : LOCAL CLI IAMADMIN-PRODUCTION

5. After createt access key, you will get two key.
    - Access Key: non-sensive
    - Secret access key: sensitive

> ⚠️ **Notice:** Anyone with both of these pieces of information can access your AWS account, so we need to be extremely careful with showing anyone on the secrect access key.

> (❗️GitHub allows you to use ***emojis*** directly in Markdown, so you can add different emojis to convey different types of notices or warnings. -- by ChatGPT)

6. The action for access keys: Edit description, Deactive, Active, Delete. If you want to suspend access for any reason, deactive and reactive is very useful. When you want to delete the access keys, you need to deactive them and then you can delete them.


7. You can only have two sets of access keys either active or inactive per identity within AWS.

## AWS CLI v2 installation

### AWS CLI v2 Windows Installation
[Windows Installation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

### AWS CLI v2 Linux Installation
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

unzip awscliv2.zip

sudo ./aws/install  
```
[Linux Installation](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)

### Verification for Installation 

``` sh
aws --version
```
The result for windows like as following:

```
aws-cli/2.10.2 Python/3.9.11 Windows/10 exe/AMD64 prompt/off
```

The result for windows like as following:

```
aws-cli/2.13.26 Python/3.11.6 Linux/6.1.54-060154-generic exe/x86_64.ubuntu.22 prompt/off
```
> ⚠️ **Notice:**  The important part is version two (aws-cli/2.xx)

### AWS CLI v2 Configuration

Our identities or users in those account is we need to configure a set of credentials which the command line interface will use to communicate with AWS. And, we can use to configure multiple aws accounts so we can have a name profile for that.

Command Line:
```
aws configure --profile iamadmin-production

```
Input the following value for each attributes:
- AWS Access Key ID 
- AWS Secret Access Key
- Default region name: us-east-1
- Default output format (using the default)

### Verification for credential

``` sh
aws s3 ls --profile iamadmin-production
```
> ⚠️ **Notice:**  If you only using the command (```aws s3 ls```), the result show is for default credential. If you don't configure default credential, the result will show error message as below:
```
Unable to locate credentials. You can configure credentials by running "aws configure".
```
