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

### checkout

checkout will authenticate with your repository and then fetch the code in checkout into the commit that trigger the workfow to run

- $GITHUB_SHA --> It is an environement variable that give the commit id
- $GITHUB_REPOSITORY --> It is an environement variable that give the user_name and the repository_name
- $GITHUB_WORKSPACE --> It is an environement variable that give the workspace directory (like pwd (Linux) or dir (Windows))
- "${{ github.token }} --> the token is used when you authenticate with your repository

---

### git checkout -b new_branch

allow to create a new branche: develop

### git checkout branche_name

allow to move to an other branche (branche_name)

---

### schedule workflow

- https://crontab.guru/
- "minutes hours day_of_the_month month day_of_the_week"

```
schedule:
    - cron: "0 * * * *"

```

---

### repository_dispatch:

- to trigger a workflow mannually with a POST request from Postman

- go to postman and create a POST request: https://api.github.com/repos/Mohamed-Amine-Dogui/GITHUB-ACTIONS-SANDBOX/dispatches
- in Headers --> key :
- - Accept --> value: application/vnd.github.v3+json
- - Content-Type --> value: application/json

```
{
  "event_type": "build"
}
```

- in Body --> click raw and choose JSON
- generate a token: https://github.com/settings/tokens/new
- postman --> Authorization --> Basic Auth --> paste the token in the password feld

---

### Filter pattern cheat sheet

https://docs.github.com/en/actions/learn-github-actions/workflow-syntax-for-github-actions#filter-pattern-cheat-sheet

You can use special characters in path, branch, and tag filters.

- \*: Matches zero or more characters, but does not match the / character. For example, Octo\_ matches Octocat.
- \*\*: Matches zero or more of any character.
- ?: Matches zero or one of the preceding character.
- +: Matches one or more of the preceding character.
- [] Matches one character listed in the brackets or included in ranges. Ranges can only include a-z, A-Z, and 0-9. For example, the range[0-9a-z] matches any digit or lowercase letter. For example, [CB]at matches Cat or Bat and [1-2]00 matches 100 and 200.
- !: At the start of a pattern makes it negate previous positive patterns. It has no special meaning if not the first character.

- The characters \*, [, and ! are special characters in YAML. If you start a pattern with \_, [, or !, you must enclose the pattern in quotes.

- pattern will match the branch feature/featAC --> feature/feat[ABC]+
- If we are filtering our workflow by path using this pattern: '\*' --> will match app.js but not src/app.js
- If we are filtering our workflow by path using this pattern: '\*\*/src/\*\*'. --> will match evrything before and after src
- If we are filtering our workflow by path using this pattern: '\*.jsx --> will match index.js
