# How-To Clone GitHub Repository
## Plus Added Cheat Sheet

## Overview
  This guide will discuss how to clone a repository from GitHub to a Mac
  using Terminal to make any changes. Some of the things that will be
  explored are uploading new files from computer to the repository, changing
  the names of folders, and much more.

  *Note: this is a working article

## Table of Contents

[How to clone a repository to computer](how-to-clone-a-repository-to-computer)
## Getting Started

### How to clone a repository to computer
  1. **Open Terminal**: You can open Terminal from the Applications > Utilities
    folder, or by using Spotlight (press `Cmd + Space`, type "Terminal", and press
    Enter).

  2. **Navigate to the desired directory**: Use the `cd` command to navigate to
    the directory where you want to clone the repository. For example, if you want
    to clone the repository into the `Documents` directory, type:
    ```sh
    cd ~/Documents
    ```

  3. **Copy the repository URL**: Go to the GitHub page of the repository you
    want to clone. Click the green "Code" button and copy the URL from the HTTPS
    tab.

  4. **Clone the repository**: Use the `git clone` command followed by the URL
    you copied. For example:
    ```sh
    git clone https://github.com/username/repository-name.git
    ```

  5. **Navigate to the cloned repository**: After cloning, navigate into the
    repository directory using the `cd` command. For example:
    ```sh
    cd repository-name
    ```
### How to upload new documents to repository


## Cheat Sheet
#### Navigate to certain folder:
  * cd ~/ExampleFolerName - this commad allows you to navigate to any folder
* __Change File Name from Terminal:__
