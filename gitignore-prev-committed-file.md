# Git-ignore a previously committed file

If you've already committed a file to your Git repository and pushed it to a remote,
adding it to `.gitignore` **won't retroactively remove it** from version control.

But you can fix that! Here's how to properly ignore it going forward:

## 🛠️ Steps to Ignore a Previously Committed File

1. Add the file to `.gitignore`

   Open your `.gitignore` file and add the path to the file you want to ignore.

   ```gitignore
   # .gitignore
   path/to/your/file
   ```

2. Remove the file from the Git index (but not from your local disk)

   Run this command:

   ```bash
   git rm --cached path/to/your/file
   ```

   This tells **Git** to stop tracking the file without deleting it from your working directory.

3. Commit the change

   ```bash
   git add -A
   git commit -m "Stop tracking file and add to .gitignore"
   ```

4. Push to the remote

   ```bash
   git push
   ```

Now Git will no longer track changes to that file, and it will be ignored in future commits.

> **⚠️ Heads-up**: If someone else pulls this change,
> Git will remove the file from their working directory unless they’ve also added it to their `.gitignore`.

## Use-case

- When you accidentally forgot to include an auto-generated file or any file to the `.gitignore`
- When you decided to include a file in `.gitignore` but it was already committed previously
