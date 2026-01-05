tag: [[AppSrv]]

To commit to GitHub via VS Code:

- **Make your initial commit** if your repo is empty:
    
    ```bash
    git add .
    git commit -m "First commit"
    ```
    
- **Rename your branch to `main`** if it defaults to `master` (after the initial commit):
    
    ```bash
    git branch -M main
    ```
    
- **Add your remote GitHub repository:**
    
    ```bash
    git remote add origin <your_github_repo_https_or_ssh_url>
    git remote -v
    ```
    
- **Push your branch:**
    
    ```bash
    git push -u origin main
    ```

To bypass SSL verification.

```bash
git config --global http.sslVerify false
```

For WSL: 

```bash
git config --global http.sslbackend gnutls
```

Checking config:

```bash
git config --global --list
```

git remote -v

git remote remove origin

git remote add origin