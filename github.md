# Using multiple github accounts on a machine

## SSH Key Settings

1. Generating a new SSH key
```sh
ssh-keygen -t ed25519 -C "your@email.com"
```

2. Adding your SSH key to the ssh-agent
```sh
eval "$(ssh-agent -s)"
```

3. Modify your ~/.ssh/config file

- Backup your ssh config
```sh
cp ~/.ssh/config ~/.ssh/config.backup
```

- Modify your ssh config
```sh
echo "Host [your_custom_domain].github.com\n    HostName github.com\n    IdentityFile ~/.ssh/id_ed25519_[your_key]\n    IdentitiesOnly yes" >> ~/.ssh/config
```

- Remove your backup ssh config
```sh
rm ~/.ssh/config.backup
```

4. Adding a new SSH key to your GitHub account

- Copy the SSH public key to your clipboard
```sh
pbcopy < ~/.ssh/id_ed25519_[your_key].pub
```

- Open github settings on browser and add this public key to.

## Clone A Repository
If your git url is `git@github.com:company/repo.git`, add `[your_custom_domain]` that defined in `~/.ssh/config` above.
```sh
git clone git@[your_custom_domain].github.com:company/your_repo.git
```

## Account Settings
```sh
git config --local user.name "Your Name"
git config --local user.email "your@email.com"
```

# Pretty log
Add these lines to `~/.gitconfig`
```
[alias]
lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(auto)%d%C(reset)' --all
lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(auto)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)'
lg = lg1
```
