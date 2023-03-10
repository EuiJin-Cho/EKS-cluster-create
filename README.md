# EKS-cluster-create
EKS-cluster-create manual


## AWS CLI v2 설치

```
sudo apt-get install -y unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

### 정상 설치 결과 확인
```
aws-cli/2.2.5 Python/3.8.8 Linux/4.4.0-19041-Microsoft exe/x86_64.ubuntu.20 prompt/off
```


## eksctl 설치
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```

### 정상 설치 결과 확인
```
0.68.0
```


## kubectl 설치
```
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.24.9/2023-01-11/bin/linux/amd64/kubectl
chmod +x ./kubectl
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
kubectl version --short --client
```

### 정상 설치 확인
```
Client Version: v1.24.9-eks-49a6c0
```


## Helm 설치
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 > get_helm.sh
chmod 700 get_helm.sh
./get_helm.sh
```



## AWS 계정 등록
```
aws configure
  AWS Access Key ID [None]: AKIASJ...E37V
  AWS Secret Access Key [None]: XLzhAqt...7g
  Default region name [None]: ap-northeast-2
  Default output format [None]: <ENTER>
```


### 정상 연결 결과 확인
```
ubuntu@seongmi_lee:~$ cd .aws/
  ubuntu@seongmi_lee:~/.aws$ ls
  ubuntu@seongmi_lee:~/.aws$ cat config
  [default]
  region = ap-northeast-2
  ubuntu@seongmi_lee:~/.aws$ cat credentials
  [default]
  aws_access_key_id = AKIASJ...E37V
  aws_secret_access_key = XLzhAq...7g
  
  ubuntu@seongmi_lee:~/.aws$ aws sts get-caller-identity
  {
      "UserId": "AID...KS26",
      "Account": "15..75",
      "Arn": "arn:aws:iam::158208647875:user/k8suser-console"
  }
```



## kubeconfig 생성
```
aws eks --region example_region update-kubeconfig --name cluster_name

// 아래 형식으로 작성
aws eks --region ap-southeast-1 update-kubeconfig --name test-eks-cluster
```

### 정상 연결 확인
```

```
