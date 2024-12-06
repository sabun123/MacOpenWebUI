# MacOpenWebUI 🚀
A quick app script that runs open-webui on Mac OS (as long as the programs are installed).

This was setup to run on an M4 Max Macbook Pro. Mileage may vary depending on Apple laptop.

# Dependencies 🏗️

The following is expected to be installed.
1. Homebrew
2. Miniforge
3. Python (3.11)
4. Open-webui
5. Ollama

Additionally, a mamba environment should have been setup.
In this case it was setup with:

```
mamba create --name openwebui python=3.11
```

🚨 Note that the system's `.zshrc` file has been setup to run mamba/conda on start so the ZSH terminal always has access to it. Refer to the end of this file for the init code if you need it.

# Running the app 🛠️
1. Download the `.dmg` file from the releases section
2. Double click it, and drag the app to the Applications folder
3. Run the app by clicking it (from Launchpad, the Dock or Spotlight)

# Modifying the app

The app script was written inside Apple's **Script Editor**.

Open **Script Editor** and then select the `.app` file inside this repository to modify the script. `MacOpenWebUI.app`

# What the app essentially does

1. Runs Ollama
2. Activates the openwebui env
3. Runs open-webui inside that env

Openwebui should now be reachable via http://localhost:8080


### Addendum

The code for the `.zshrc` file to allow mamba/conda to run on start.

```
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/opt/homebrew/Caskroom/miniforge/base/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/homebrew/Caskroom/miniforge/base/etc/profile.d/conda.sh" ]; then
        . "/opt/homebrew/Caskroom/miniforge/base/etc/profile.d/conda.sh"
    else
        export PATH="/opt/homebrew/Caskroom/miniforge/base/bin:$PATH"
    fi
fi
unset __conda_setup

if [ -f "/opt/homebrew/Caskroom/miniforge/base/etc/profile.d/mamba.sh" ]; then
    . "/opt/homebrew/Caskroom/miniforge/base/etc/profile.d/mamba.sh"
fi
# <<< conda initialize <<<
```