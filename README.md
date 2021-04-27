# Vim-Jetbrains-Deployment
Trying to migrate from Jetbrains applications to vim and need deployment over SSH?
Well I'm kinda trying to get that working.
*Please note that I'm not a good programmer! Feel free to contribute to the project*

---

**TLDR**

The plugin will look for the configuration located in .idea (generated by jetbrains), use the SFTP / SSH config for uploading and downloading from the server.
Ideally, you will be using this plugin, and calling `:call JB_SFTP_DownloadFile()` and `:call JB_SFTP_UploadFile()` to fast and quickly make updates to the server files.

## Dependencies
- scp

## Possible dependencies
- sed

## Setting up
**Setting up with Plugin manager**

    Plug 'D3faIt/Vim-Jetbrains-Deployment'

**Setting up manually**

Download the `JB_SFTP.vim` script, put it inside desired folder and source it in `init.vim` / `.vimrc`
For example:

    source $HOME/.config/nvim/scripts/JB_SFTP.vim

---

**Setting syncing**
1. First you need to cd to the directory where the project is located.
2. Then you can setup the config by doing `:call JB_SFTP_Setup()` or, if the .idea folder exists within the folder, you can generate the config by doing `:call JB_SFTP_GenerateConfig()`
3. You need to setup generate a ssh key identity file, this will be asked automatically anyways, but you can do it manually with `:call JB_SFTP_GenerateSSHKeyFile()`
4. Then, you can sync all hashsums for both directories locally and remote, do `:call JB_SFTP_SyncAll_sha256sum()` (Depending on the project size, this might take up to around 30 minutes)

## Mapping example

    map <C-S> <Esc>:call JB_SFTP_UploadFile()<CR>
    imap <C-S> <Esc>:call JB_SFTP_UploadFile()<CR>
    map <C-M> <Esc>:call JB_SFTP_DownloadFile()<CR>
    imap <C-M> <Esc>:call JB_SFTP_DownloadFile()<CR>

## Usage
Download the file from the server with call `:call JB_SFTP_DownloadFile()`, or upload with `:call JB_SFTP_UploadFile()`

## Known issues
- Not tested on MacOS or Windows
- Only supports SSH setup

---
The project is in incredible early stages, this is only tested on my system with my config. Please, if you see something that can be improved, contribute to the code.
