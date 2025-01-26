# Setting up a dev container for Rust

* Primary author: [Nate Hicks](https://github.com/hicksnat)

* Reviewer: [Bryson Hogsed](https://github.com/brysonth)

## Requirements
Make sure you have:  
1. Docker  
2. VSCode  
3. Dev container extension for VSCode  

## Making your directory and git repository
1. Open your terminal
2. Create your directory:  
`mkdir <directory-name>`  
`cd <directory-name>`
3. Create your git repository  
`git init`

## Creating your dev container
1. Open VSCode
2. Open the directory you just made
3. Within your directory, create another directory named `.devcontainer`
4. Inside `.devcontainer`, create another file called `devcontainer.json`  
5. Copy and paste the following code into the `devcontainer.json` file: 

```
{
  "name": "Rust Dev Container",
  "image": "rust:latest",
  "features": {
    "ghcr.io/devcontainers/features/docker-in-docker:1": {}
  },
  "postCreateCommand": "cargo init && cargo build",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": [
        "rust-lang.rust-analyzer"
      ]
    }
  }
}
```

## Reopen your work in a container
1. Press Ctrl + Shift + P (Cmd + Shift + P on Mac) and search for the option "Reopen in Dev Container"  
After clicking this option, your dev container should be all set up! Now let's run something basic in Rust

## Hello world
1. Create a new directory in your container called `src`  
2. Create file within `src` name `main.rs`
3. Paste the following code into `main.rs`  
`fn main() {`  
    `println!("Hello, World!");`  
`}`  
4. All that's left to do is open the VSCode terminal and run the command `main run`



## Notes: It looks good to me! I would change it so that it tells you to cd into the src directory
##        and then it tells you to use ./main to run the program