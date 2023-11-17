### How to Use Github's SSH feature (Windows)

This tutorial will show you how to push using Github's SSH feature allowing you to bypass typing in the password each time. It will go through the steps of generating an SSH key and adding it to your Github Settings. 

1. **Open Git Bash** or your terminal.

2. **Generate  SSH Key**:
   - Run:
     ```
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     ```
   - Replace `"your_email@example.com"` with the email associated with your GitHub account.
   - When prompted to "Enter a file in which to save the key," press `Enter` to accept the default file location.
   - Enter a passphrase when prompted (optional but recommended for additional security).

3. **Ensure the SSH Agent is Running**:
   - Start the ssh-agent in the background using:
     ```
     eval "$(ssh-agent -s)"
     ```
   - You should see a message like "Agent pid #####," indicating the agent has started.

4. **Add Your SSH Key to the ssh-agent**:
   - If you accepted the default file location in step 2, add your SSH key to the ssh-agent using:
     ```
     ssh-add ~/.ssh/id_rsa
     ```

### Adding the SSH Key to Your GitHub Account

1. **Copy the SSH Key to Your Clipboard**:
   - Use the following command to copy the content of your public SSH key to the clipboard:
     ```
     clip < ~/.ssh/id_rsa.pub
     ```
   - This will copy the contents of the `id_rsa.pub` file, which is your public SSH key.

2. **Add the SSH Key to GitHub**:
   - Go to [GitHub](https://github.com/) and sign in.
   - Click on your profile photo, then click **Settings**.
   - In the user settings sidebar, click **SSH and GPG keys**.
   - Click **New SSH key** or **Add SSH key**.
   - In the "Title" field, add a descriptive label for the new key.
   - Paste your key into the "Key" field.
   - Click **Add SSH key**.

### Testing the Connection

- Once the key is added to GitHub, test your SSH connection:
  ```
  ssh -T git@github.com
  ```
- May receive a warning about the authenticity of the host. Type `yes` to continue. If everything is set up correctly, you should see a message confirming your successful authentication.

### Using SSH with Your Repositories

- For existing repositories cloned using HTTPS, change them to use SSH:
  ```
  git remote set-url origin git@github.com:username/repository.git
  ```
  Replace `username` and `repository` with your GitHub username and repository name.

Now your SSH key is set up, and you can securely connect to GitHub without using your username and password for each operation.


- If you need to create a new repository, open up bash in your specified folder
  ```
  git init
  git add . 
  git commit -m "init"
  git remote add origin git@github.com:username/repository.git
  git push -u origin main
  ```
