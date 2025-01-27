# Setting up a dev container for Rust

* Primary author: [Trisha](https://github.com/trisv1)

* Reviewer: [Cassidy Lowe](https://github.com/calowe2)

## Step by step tutorial on how to set up a Dev Container for Rust

### Important:

You will not need to install anything directly to your host machine since we are using a Dev Container. Since we are running Linux in our Dev Container, you should not expect to see a .exe file.
!!! note

    Make sure you do not install anything! If you install directly to your host machine you are following this tutorial wrong. 

### Rust 

Rust is a programming language that acts as an alternative to C and C++ in many applications. It is used due to its superior performance, memory safety, and its concurrency.

#### What you need to have installed before you continue:

* VSCode
* Docker (must be running)
!!! IMPORTANT
    MAKE SURE DOCKER IS RUNNING!
    
* Git  


### Step 1: Creating a Directory, Initializing Git, and Creating a Readme

Run the following commands in your system's terminal:

``` yaml
mkdir rust-project
cd rust-project # (1)
```

1.   We have created and entered a new directory for the rest of our setup.

Next, run the following command

``` yaml
git init # (1)
```

1.   This is the git initialization command

Create a Readme file with the following code 

``` yaml
echo "# Rust README"> README.md
git add README.md
git commit -m "Initial commit with README" # (1)
```

### Step 2: Setting up a Remote Repository on GitHub

* Enter your internet browser and log into your github account. Navigate to the "Create a new repository" page. 

* Specify the following:

    **Repository Name:** rust-project

    **Description:** "Setting up a devcontainer for Rust."

    **Visibility:** Public

* Do not initialize the repository with a README, .gitignore, or license. 

* Click create repository  


### Step 3: Add the GitHub Repository as a Remote  

* Run the following command in your terminal, replacing the "your-username" with your GitHub username: 

``` yaml
git remote add origin https://github.com/<your-username>/go-project.git # (1)
```

Check your default branch name with the subcommand git branch. If it's not main, rename it using the following command: 

``` yaml
git branch -M main.
``` 

Commit and push these changes to the GitHub repository by running the following command:

``` yaml
git push --set-upstream origin main # (1)
```

### Step 4: Adding a Dev Container Config  
1. In VS Code, open the rust-project directory. (File > Open Folder).

1. Install the Dev Containers extension for VS Code.
    
1. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:

**.devcontainer/devcontainer.json**

Add the following code to your devcontainer.json file:

``` yaml
{
	"name": "Rust Development Environment",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
        "vscode": {
            "extensions": [
                "rust-lang.rust-analyzer"
            ]
        }
    }
}

```  
This file sets up your dev container environment ensuring that it is consistent and reproducible. Here we specify that the name of our dev container is "Rust Project". Image is the image Docker is going to use, customizations adds useful configurations to VS Code such as telling it to use the Rust Language Analyzer, and our extensions installs Rust in the container so that we do not need to install on our host machine.  

### Step 5: Reopen the Dev Container

Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option.  

Run the Command 

``` yaml
rustc --version
```

to prove a recent version of Rust


### Step 6: Try it Out by Adding a Hello World Example

Create a new Hello World directory using the following command

``` yaml
cargo new hello_world --vcs none
```

Next move into the hellow-world directory with the following command:

``` yaml
cd hello_world
```

There should already exist a main.rs file with the following code:

``` yaml
fn main() {
    println!("Hello, world!");
}
```

### Step 7: Compile and Run Your Project 

Run the following code to compile and run your project!

``` yaml
cargo build
```

This command is similar to the command gcc which we learned in 211. This generates an exectuable which can be run with the next command:

``` yaml
cargo run
```

You should see "Hello World" printed. 

### Step 8: Let's Save Our Work!

Enter the following code in your terminal to commit

``` yaml
git add .
git commit -m "Hello World in Rust!"
```

**Note**: If you get the following error

fatal: detected dubious ownership in repository at '/workspaces/go-project'
To add an exception for this directory, call: git config --global --add safe.directory /workspaces/go-project

Run the code as it says 

``` yaml
git config --global --add safe.directory /workspaces/go-project
```

Then add and commit as stated above ^

Finally, run

``` yaml
git push origin main # (1)
```

1. Now our Github has all of our work!