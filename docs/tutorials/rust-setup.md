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
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
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
2. Check that you have a recent version of Rust. In the VSCode dev container terminal, run the command `rustc --version`  
The output should look something like `rustc 1.84.0 (13nd7h469 2025-01-07)`. If your version is significantly
older than this, consider updating it.

## Hello world
1. If it does not already exist, create a new directory in your container called `src`  
2. Create a file within `src` named `main.rs`
3. Paste the following code into `main.rs`  
`fn main() {`  
    `println!("Hello, COMP423!");`  
`}`  
4. In the VSCode terminal, run the command `cargo build`. This essentially compiles your program
5. Now, cd out of your src directory by running `cd ..`
6. Once you are in the folder that simply has the name of your project, you can run the command
straight from there by running `./target/debug/<project-name>` in the VSCode terminal
7. Alternatively, you can use the command `cargo run` to run your project, which essentially combines building and running the binary into one step. In general, `cargo run` is more efficienct, while the method in step 6 gives you more control and allows you to look over your built files/ binary.



<!-- Notes: It looks good to me! I would change it so that it tells you to cd into the src directory and then it tells you to use ./main to run the program-->