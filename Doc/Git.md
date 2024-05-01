# Git

## Git Commands

### Check version

`$ git version`

### Update git

`$ git update-git-for-windows`

### Setting line endings

`$ git config --global core.autocrlf true`
On Windows, you simply pass true to the configuration as above.
This auto-converts CRLF line endings into LF when you add a file and auto-converts LF endings into CRLF when you check out code.
For detail, read [Configuring Git to handle line endings](https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings)

### Setting user name and email address

```TEXT
$ git config --global user.name "matsumotominoru"
$ git config --global user.email "email@example.com"
```

If you omit "--global", you can apply this to the local repogitory in the current working directory.

### Commit Date

- Set AuthorDate(mainly used date)
Alter author date in commit object, do not alter committer date in commit object or commit date in `.git\logs`.
`$ git commit -m "Test" --date=format:short:2006-07-03`

- View two dates
`$ git log --pretty=fuller`

### Get a deleted or modified file from specified git commit

`$ git checkout CommitHash -- FilePath`
For detail, read [Oh shit, I need to undo my changes to a file!](https://ohshitgit.com/#undo-a-file)

### Get changed files only (omit diff)

`$ git log --name-only`

For more similar command, read [How to have 'git log' show filenames like 'svn log -v'](https://stackoverflow.com/questions/1230084/how-to-have-git-log-show-filenames-like-svn-log-v)

### Set Git HEAD to Specific Commit ID

`$ git reset --hard ToBeHeadedToCommitSHA`

For git reset details, read [Git Reset](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset)

`$ git diff COMMIT1_SHA1..COMMIT2_SHA1 --name-only`

### View git objects

Git object is blob(file contents) or tree or commit.
Each git object is assigned 40-digit SHA-1 ID and stored in `.git\objects`. First two digit of SHA-1 is directory name.
We can get object content by
`$ git cat-file -p [object_sha_1_40_digit]`

Commit object SHA-1 ID is viewed by 
`$ git log --all`
or located in `.git\logs`.

### Unpack packfiles

Move .pack file to top directory in the repo.(empty pack directory)
Run following command
`$ git unpack-objects < *.pack`
Objects will be expanded in `.git\objects`.

## GitHub CLI

### List GitHub repo

`$ gh repo list User --limit MaximunNumberOfOutputLines`
[mannual](https://cli.github.com/manual/gh_repo_list)

## GitHub REST API

### Get following users list

`$ curl https://api.github.com/users/{userName}/following`
