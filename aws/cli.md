# [Home](../README.md) > AWS Cli

1. Setting up Profiles
    1. Create a new profile
        ```bash
        aws configure --profile <profile-name>
        # Replace <profile-name> with the desired profile name.
        ```
    2. Set the default profile
        ```bash
        export AWS_PROFILE=<profile-name>
        # Replace <profile-name> with the desired profile name.
        ```
    3. Show the current profile
        ```bash
        aws configure list
        ```

    4. Be aware that the profile and the credentials should be saved in `~/.aws/credentials` and `~/.aws/config` respectively.
        - If you ever to customize/change these folders they should look like the following
        ```bash
        # ~/.aws/config
        [profile gather]
        region = us-west-1
        output = json

        [profile cointosis]
        region = us-west-2
        output = json
        ```
        ```bash
        # ~/.aws/credentials
        [gather]
        region = us-west-1
        aws_access_key_id = <access_key>
        aws_secret_access_key = <secret_key>

        [cointosis]
        region = us-west-2
        aws_access_key_id = <access_key>
        aws_secret_access_key = <secret_key>
        ```

2. Random tools for ZSHRC
    1. Get the current profile
        ```bash
        function getprofiles {
          cat ~/.aws/config | grep profile
        }
        ```
    2. Set the profile you want from the available options
        ```bash
        function setprofile {
          export AWS_PROFILE="$1"
          env | grep AWS_PROFILE
          aws configure list
          export AWS_REGION=$(aws configure get region)
          env | grep AWS_REGION
        }
        ```
    3. Login to ECR
        ```bash
        function ecrlogin {
          aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin 043337637715.dkr.ecr.us-west-2.amazonaws.com
        }
        ```