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
	"name": "Rust Project",
	"image": "mcr.microsoft.com/devcontainers/rust:latest",
	"customizations": {
        "vscode": {
        "settings": {
        "go.useLanguageServer": true
    },
    "extensions": [
      "rust-lang.rust-analyzer"
    ]
  }
}
}
```  