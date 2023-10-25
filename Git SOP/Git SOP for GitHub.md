NOTE: Where text is in ALL CAPITALS, please replace with the logical equivalent.

On Linux:
```bash
ssh-keygen -t ed25519 -C "GITHUB_USERNAME@github.com"
> /home/LOCAL_USERNAME/.ssh/KEYNAME
> <password>
> <password>
ssh-add /home/LOCAL_USERNAME/.ssh/KEYNAME
git clone git@github.com:USERNAME/REPO.git
> yes
# I didn't need to provide the password again, but others may have to
cd Manet9785-23-7/
git config --global user.name "USERNAME"
git config --global user.email "USERNAME@EMAILPROVIDER"
git checkout -b testing-USER
# "-b" only required when creating a new branch
git add <changed file(s)>
git commit -m "<Brief, but descriptive message>"
# Ensures the origin branch is up-to-date
git push origin testing-USER

# To sync with the remote repository, use the following command: "git pull origin testing-USER"
# If the branch is no longer required (branches are _supposed_ to be used for implementing specific features of software, so would be named after that feature), execute the following command to remove the branch: "git branch -d testing-USER"
```

On GitHub.com:
1. Authenticate on Github, and navigate to your repostory
2. Select "Pull Requests" tab
3. Click "New Pull Request"
4. Select the desired "base repository" (the local one; "REPO")
5. Select the desired "compare" branch ("testing-USER")
6. Add comments, and Select "Create Pull Request"
7. Ask someone else to complete the merge
	- If I'm the one merging (as opposed to requesting a merge), there'll be a pull request in the "Pull Requests" tab - select it, add comments, and decide to merge or not