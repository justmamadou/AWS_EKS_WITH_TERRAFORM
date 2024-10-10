### Create IAM User
```bash
aws iam create-user --user-name manager
```

###  Create an access key for the IAM user
```bash
aws iam create-access-key --user-name manager
```

### Configure the developer profile
```bash
aws configure --profile manager
```

### Check if manager can assume eks-admin IAM role
```bash
aws sts assume-role \
--role-arn arn:aws:iam::ACCOUNT_ID:role/dev-demo-eks-admin \
--role-session-name manager-session \
--profile manager
```

### Add AWS profile manuelly
```bash
 vim ~/.aws/config
```
#### Add the following
```bash
[profile eks-admin]
--role-arn arn:aws:iam::ACCOUNT_ID:role/dev-demo-eks-admin \
source_profile = manager
```

### Update eks config
```bash
aws eks update-kubeconfig \
--region eu-west-1 \
--name dev-demo \
--profile eks-admin
```

### Check if the correct profile is used in eks
```bash
kubectl config view --minify
```