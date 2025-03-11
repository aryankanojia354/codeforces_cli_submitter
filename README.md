# Codeforces Cli Submitter

Tool to submit to online judges dirrectly from command line

## Prerequisites

You would need [rust](https://www.rust-lang.org/tools/install) and [docker](https://docs.docker.com/desktop/)

### 1. Install Rust
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
### 2. Update your PATH
```sh
export PATH="$HOME/.cargo/bin:$PATH"
```
### 3. Reload the shell
```sh
source ~/.bashrc  # If using Bash
source ~/.zshrc   # If using Zsh
```

## Installation
```
cargo install --git https://github.com/aryankanojia354/codeforces_cli_submitter.git
```

## Usage
```
submitter <task url> <language> <path to solution>
```

## Usage Second Method ( Make a Bash Script for common path to solution , language )

### 1. Open your shell configuration file
```sh
nano ~/.bashrc  # If using Bash
nano ~/.zshrc   # If using Zsh
```

### 2. Add the following function in last of all the PreExisting code
```sh
cfsubmit() {
  if [ "$#" -ne 2 ]; then
    echo "Usage: cfsubmit <contest_id> <problem_letter>"
    return 1
  fi
  local contest_id="$1"
  local problem_letter="$2"
  local base_url="https://codeforces.com/group/MWSDmqGsZm/contest"
  local url="${base_url}/${contest_id}/problem/${problem_letter}"
  # Set your defaults here:
  local language="C++20"
  local file="solution.cpp"
  submitter "$url" "$language" "$file"
}
```
### 3. Save and exit

Press **CTRL + X**, then **Y**, and hit **Enter**.

### 4. Reload the shell
```sh
source ~/.zshrc  # For Zsh users
source ~/.bashrc  # For Bash users
```
## Usage(only for codeforces , cpp language ...)
Make sure you have your solution file **solution.cpp** in the current directory.  

Then, run the command:
```sh
cfsubmit 219432 D
```
This will submit **solution.cpp** for problem **D** in contest **219432** using **C++20**.

---

## Supported sites(Bash Script is only for the codeforces website)

At the moment the following is supported:

- Codeforces
- Codechef
- Yandex Contest
- AtCoder
- Universal Cup
- Toph*

*no support for specifying language, language of the last submit is used

If doesnot work then retry , It first take time but when you use it after your first submittion then it will work smoothly.
This is due to cloudflare captcha
