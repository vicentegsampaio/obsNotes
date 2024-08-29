### **Study Points**

1. **Basic Git Commands:**
    - **init** - >initializes a new git repository in the current directory, the first command u will run to start version controlling a project
    
    - **clone** repository-url -> creates a copy a remote repository in your machine
    
    - **add** (file-name or .) -> stages changes (new, modified or deleted) for the next commit 
    
    - **commit** -m "message" -> records the changes made to the files in the repository. each one includes a message that describes what changes were made 
    
    - **status** -> Displays the status of changes in the working directory and the staging area. It shows which files are modified, staged, or untracked.
    
    - **push** origin branch-name -> sends your committed changes to a remote repo
    
    - **pull** origin branch name -> fetches and integrates changes from a remote repo into ur current branch
    
    - **merge** branch name ->combines changes from one branch onto another
    
    - **branch** -> lists all branches in ur repo or creates a new branch
    
    - **checkout** switches to another branch and return files to a previous state
    
    - **stash** -> temporally saves ur changes without committing them, allowing you to switch branches without losing work
    
    - **log** -> display the commit history of ur repo in the current branch
    
    - **reset** -> reset --soft commit-hash -> Resets to a commit, keeping changes in the staging area git reset --hard commit-hash -> Resets to a commit, discarding all changes
    
    - **revert** -> creates a new commit that undoes the changes from a previous commit, safer than reset cause doesn't rewrite history
    
    - **rebase** -> moves or combines a sequence of commits to a new base commit. git checkout feature-branch git rebase target-branch # Rebase feature branch onto target branch
    
    - **cherry-pick** -> Allows you to apply changes from a specific commit in another branch without merging the whole branch.
    
    - **fetch** ->  Fetches changes from the remote repository without merging them into your working directory. This command updates your local repository’s knowledge of the remote repository.
    
    - **diff** -> show the differences between staging and working directory or two branches
    
    - **remote** -> manages connections to remote repositories. 
    
    - **merge** --squash -> Combines all changes from a branch into a single commit. This is useful for cleaning up the commit history when merging a feature branch.
	
    
2. **Semantic Versioning:**
    
    - Importance of branches in feature development.
    - Merging strategies: fast-forward, three-way merge, and resolving conflicts.
3. GitFflow:**
    
    - How to fork repositories and create pull requests.
    - Understanding the significance of `Issues` for project management.
    - Familiarize with GitHub Actions for automating workflows.
4. Trunk Based:**
    
    - Writing meaningful commit messages.
    - Regularly pushing changes to remote repositories.
    - Branch naming conventions and branching strategies (e.g., Git Flow).
5. **Collaborating on GitHub:**
    
    - Setting up and managing repositories on GitHub.
    - Reviewing and merging pull requests.
    - Using GitHub Pages for documentation or project websites.
6. **Security and Access Control:**
    
    - Understanding repository permissions (public vs. private).
    - Managing SSH keys and Personal Access Tokens (PAT) for secure access.