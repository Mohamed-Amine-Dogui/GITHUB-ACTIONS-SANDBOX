# GITHUB-ACTIONS-SANDBOX

#########################################################################

### command

#########################################################################

- git status : Show the changes
- git add -A : add All changes
- git reset . : do the opposit of git add
- git commit -m "first commit": give a name to the commit (changes)
- git push : uplowad the changes in to the repository

---

### Generate a SSH public key

- 1 - Powershell --> ssh-keygen
- 2 - just press enter until you get a key generated (no need to make any input)
- 3 - Go to C:\Users\mdogui/.ssh --> Copie the content of id_rsa.pub
- 4 - Go to the Browser --> Github
- 5 - Setting --> SSH and GPC Keys --> New SSH Key
- 6 - Paste the content of id_rsa.pub and give a name e.g. "my_laptop"

---

### Start your project

git clone https://github.com/Mohamed-Amine-Dogui/github-actions-test.git

- 1- git add -A : add All
- 2- git commit -m "first commit"
- 3- git push

---

### configure the credential

- aws configure --profile MyAWS
- AWS Access Key ID [****************VAPA]: XXXXXX
- AWS Secret Access Key [****************EG7c]: XXXXXX
- Default region name [us-west-1]: eu-west-1
- Default output format [None]: json

go to : C:\Users\mdogui\.aws and you will finde cofig and credentials

- Now create provider.tf and it write:

```
provider "aws" {
  region  = "eu-west-1"
  profile = "MyAWS"
}
```

---
