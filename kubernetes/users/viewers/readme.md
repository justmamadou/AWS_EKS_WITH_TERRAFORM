### Create IAM User
```bash
aws iam create-user --user-name developer
```

###  Create an access key for the IAM user
```bash
aws iam create-access-key --user-name developer
```

### Configure the developer profile
```bash
aws configure --profile developer
```

### Verifiy the profil was correctly configure
```bash
aws sts get-caller-identity --profile developer
```

### Connect to eks cluster using the developer profile
```bash
aws eks update-kubeconfig --region eu-west-1 --name dev-demo --profile developer
```

### Check if the correct profile is used in eks
```bash
kubectl config view --minify
```