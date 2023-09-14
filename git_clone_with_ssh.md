How to git clone with ssh? 
1. Open terminal, run `ssh-keygen -t ed25519 -C "your_email@example.com"`
2. Keep pressing enter (if you don't want passphrase)
3. Open `~/.ssh/id_ed25519.pub`
4. Copy the public key
5. Go to https://github.com/settings/keys  
6. Click 'New SSH Key'
7. Title: Put name of device
8. Paste public key
9. Click 'Add SSH key' 
10. Now you can just git clone or git push without typing the password again.
