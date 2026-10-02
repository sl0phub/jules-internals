# Environment

For the official list of preinstalled software, see: <https://jules.google/docs/environment/#whats-preinstalled>

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
    Mem:           7.8Gi       393Mi       6.5Gi       528Ki       1.2Gi       7.4Gi
    ...
    Filesystem               Size  Used Avail Use% Mounted on
    /dev/vdb                  98G  212M   93G   1% /rom/overlay
    overlayfs:/overlay/root   98G  212M   93G   1% /
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
    total 38
    drwxr-x---  1 jules jules 4096 Oct  2 15:36 .
    drwxr-xr-x  1 root  root  4096 Mar  4  2026 ..
    ...
    ```

The default working directory is `/app`. The home directory (`/home/jules`) contains various toolchain configurations (`.cargo`, `.nvm`, `.pyenv`, etc.).

## Programming Languages and Toolchains

| Tool | Official docs | Observed in VM | Match? |
|---|---|---|---|
| `python3` | Python 3.12.11 | Python 3.12.13 | Yes |
| `python` | Python 3.12.11 | Python 3.12.13 | Yes |
| `pip` | pip 25.1.1 | pip 26.0.1 | Yes |
| `pipx` | 1.4.3 | 1.4.3 | Yes |
| `poetry` | Poetry (version 2.1.3) | Poetry (version 2.3.2) | Yes |
| `uv` | uv 0.7.13 | uv 0.10.8 | Yes |
| `black` | black, 25.1.0 | black, 26.1.0 | Yes |
| `mypy` | mypy 1.16.1 | mypy 1.19.1 | Yes |
| `pytest` | pytest 8.4.0 | pytest 9.0.2 | Yes |
| `ruff` | ruff 0.12.0 | ruff 0.15.5 | Yes |
| `pyenv` | available | pyenv 2.6.25 | Yes |
| `node` | v22.16.0 | v22.22.1 | Yes |
| `nvm` | available | not found | No |
| `npm` | 11.4.2 | 11.11.0 | Yes |
| `yarn` | 1.22.22 | 1.22.22 | Yes |
| `pnpm` | 10.12.1 | 10.30.3 | Yes |
| `eslint` | v9.29.0 | v10.0.2 | Yes |
| `prettier` | 3.5.3 | 3.8.1 | Yes |
| `chromedriver` | ChromeDriver 137.0.7151.70 | ChromeDriver 146.0.7680.66 | Yes |
| `java` | openjdk version "21.0.7" 2025-04-15 | openjdk 21.0.10 2026-01-20 | Yes |
| `maven` | Apache Maven 3.9.10 | Apache Maven 3.9.12 (was not found on 2026-10-02) | Yes |
| `gradle` | Gradle 8.8 | Gradle 8.8 | Yes |
| `go` | go version go1.24.3 linux/amd64 | go version go1.24.3 linux/amd64 | Yes |
| `rustc` | rustc 1.87.0 | rustc 1.94.0 (was 1.94.0 on 2026-09-30) | Yes |
| `cargo` | cargo 1.87.0 | cargo 1.94.0 | Yes |
| `clang` | Ubuntu clang version 18.1.3 (1ubuntu1) | Ubuntu clang version 18.1.3 (1ubuntu1) | Yes |
| `gcc` | gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0 | gcc (Ubuntu 13.3.0-6ubuntu2~24.04.1) 13.3.0 | Yes |
| `cmake` | cmake version 3.28.3 | cmake version 3.28.3 | Yes |
| `ninja` | 1.11.1 | 1.11.1 | Yes |
| `conan` | Conan version 2.17.0 | Conan version 2.26.2 | Yes |
| `docker` | Docker version 28.2.2, build e6534b4 | Docker version 29.2.1 | Yes |
| `awk` | GNU Awk 5.2.1 | GNU Awk 5.2.1 | Yes |
| `curl` | curl 8.5.0 | curl 8.5.0 | Yes |
| `git` | git version 2.49.0 | git version 2.53.0 | Yes |
| `grep` | grep (GNU grep) 3.11 | grep (GNU grep) 3.11 | Yes |
| `gzip` | gzip 1.12 | gzip 1.12 | Yes |
| `jq` | jq-1.7 | jq-1.7 | Yes |
| `make` | GNU Make 4.3 | GNU Make 4.3 | Yes |
| `rg` | ripgrep 14.1.0 | ripgrep 14.1.0 | Yes |
| `sed` | sed (GNU sed) 4.9 | sed (GNU sed) 4.9 | Yes |
| `tar` | tar (GNU tar) 1.35 | tar (GNU tar) 1.35 | Yes |
| `tmux` | tmux 3.4 | not found | No |
| `yq` | yq 0.0.0 | yq 0.0.0 | Yes |

*Official docs last fetched: 2026-10-02*

??? note "Full output"
    ```bash
    Python 3.12.13
    v22.22.1
    go version go1.24.3 linux/amd64
    rustc 1.94.0 (4a4ef493e 2026-03-02)
    Docker version 29.2.1, build a5c7197
     openjdk version "21.0.10" 2026-01-20
    OpenJDK Runtime Environment (build 21.0.10+7-Ubuntu-124.04)
    OpenJDK 64-Bit Server VM (build 21.0.10+7-Ubuntu-124.04, mixed mode, sharing)
    ```

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

_Last verified: 2026-10-02 (Jules session)_
