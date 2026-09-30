# Environment

This page documents the environment where Jules runs.

## Operating System

!!! success "Observed"
    ```bash
    $ uname -a; cat /etc/os-release
    Linux devbox 6.8.0 #1 SMP PREEMPT_DYNAMIC Fri Feb 20 20:38:43 UTC 2026 x86_64 x86_64 x86_64 GNU/Linux
    PRETTY_NAME="Ubuntu 24.04.4 LTS"
    NAME="Ubuntu"
    VERSION_ID="24.04"
    ...
    ```

## Hardware and Resources

!!! success "Observed"
    ```bash
    $ nproc; free -h; df -h
    4
                   total        used        free      shared  buff/cache   available
    Mem:           7.8Gi       375Mi       7.0Gi       528Ki       696Mi       7.4Gi
    ...
    Filesystem               Size  Used Avail Use% Mounted on
    /dev/vdb                  98G  197M   93G   1% /rom/overlay
    overlayfs:/overlay/root   98G  197M   93G   1% /
    ...
    ```

The system provides 4 CPU cores, roughly 8GB of RAM, and about 98GB of disk space.

## User Permissions

!!! success "Observed"
    ```bash
    $ whoami; id; sudo -n true && echo "passwordless sudo"
    jules
    uid=1001(jules) gid=1001(jules) groups=1001(jules),27(sudo),103(docker)
    passwordless sudo
    ```

Jules runs as user `jules` (uid 1001) and has passwordless `sudo` privileges.

## Filesystem and Working Directory

!!! success "Observed"
    ```bash
    $ pwd; ls -la ~; ls -la /
    /app
    total 26
    drwxr-x---  1 jules jules 4096 Sep 30 16:04 .
    drwxr-xr-x  1 root  root  4096 Mar  4  2026 ..
    ...
    ```

The default working directory is `/app`. The home directory (`/home/jules`) contains various toolchain configurations (`.cargo`, `.nvm`, `.pyenv`, etc.).

## Programming Languages and Toolchains

!!! success "Observed"
    ```bash
    $ python3 --version; node --version; go version; java -version; rustc --version
    Python 3.12.13
    v22.22.1
    go version go1.24.3 linux/amd64
    rustc 1.94.0 (4a4ef493e 2026-03-02)
     openjdk version "21.0.10" 2026-01-20
    ```

Available languages and versions:
- Python 3.12.13
- Node.js v22.22.1
- Go 1.24.3
- Rust 1.94.0
- Java 21.0.10

## Environment Variables

!!! success "Observed"
    ```bash
    $ env | cut -d= -f1 | sort
    ANDROID_HOME
    BUN_INSTALL
    CHROME_EXECUTABLE
    DEBUGINFOD_URLS
    DOTNET_BUNDLE_EXTRACT_BASE_DIR
    DOTNET_ROOT
    FLUTTER_HOME
    GIT_TERMINAL_PROMPT
    HOME
    JAVA_HOME
    JULES_SESSION_ID
    LANG
    LESSCLOSE
    LESSOPEN
    LOGNAME
    LS_COLORS
    MAIL
    NVM_BIN
    NVM_CD_FLAGS
    NVM_DIR
    NVM_INC
    OLDPWD
    PATH
    PWD
    SHELL
    SHLVL
    SUDO_COMMAND
    SUDO_GID
    SUDO_UID
    SUDO_USER
    TERM
    TERM_PROGRAM
    TERM_PROGRAM_VERSION
    TMUX
    TMUX_PANE
    USER
    _
    ```

## Network Access

!!! success "Observed"
    ```bash
    $ curl -I https://google.com
    HTTP/2 301
    location: https://www.google.com/
    content-type: text/html; charset=UTF-8
    ...
    ```

The environment has outbound internet access.

_Last verified: 2026-09-30 (Jules session)_