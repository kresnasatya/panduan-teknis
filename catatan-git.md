## Git Commit
Standards conventions of commit messages:
  1. Must be in quotation marks.
  2. Written in the present tense.
  3. Should be brief (singkat) (50 characters or less) when using -m

------------------------------------------------------ **GIT GLOSSARY** ----------------------------------------------------------------

```git checkout HEAD filename```: Discards changes in the working directory

```git reset HEAD filename```: Unstages file changes in the staging area

```git reset SHA```: Can be used to a previous your commit history

```git branch```: List all a Git projects branches

```git branch branch_name```: Create a new branch

```git checkout branch_name```: Used to switch from one branch to master or from one branch to another branch

```git init```: Creates a new git repository

```git status```: Inspects the contents of the working directory and staging area

```git add```: Adds files from working area to the staging area

```git diff```: Shows the difference between the working area and staging area

```git commit```: Permanently stores file changes from staging area in repository

```git log```: Shows lists of all previous commits

```git branch -d name_branch```: Delete non active branch

```git branch -m <oldname> <newname>```: Rename non active branch

```git branch -m <newname>```: Rename active branch

***CHANGE REMOTE GIT***
```git remote set-url origin git://new.url.here```

***DELETE BRANCH REMOTE AND LOCAL***
```git push origin --delete <branch_name>
   git branch -d <branch_name>```

------------------------------------------------------ **GIT WORKFLOW** ----------------------------------------------------------------

  1. WORKING AREA => Make changes to: +additions, -deletions, modifications
  2. STAGING AREA => Bring changes into the staging area
  3. REPOSITORY => Save changes to the repository as a 'commit'

------------------------------------------------------ **MERGE CASE** ----------------------------------------------------------------

```git merge branch_name```: Used to join file changes from one branch to another <br>
   Contoh:<br>
      Ada 2 branch:<br>
      * dev <= aku ada di sini<br>
      * master<br>
    Aku ingin memasukkan yang ada di branch dev ke branch master.<br>
    Langkah-langkahnya:
      1. Pastikan yang ada di branch **dev** sudah di commit. <br>
      2. Lakukan ```git checkout master``` untuk pindah ke branch **master**. <br>
      3. Lakukan ```git merge dev``` untuk menggabungkan yang ada di **dev** ke dalam **master**
